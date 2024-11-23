
# Code chương trình 3 use case lab1:

class Transaction {

    private LocalDate date;
    private double amount;
    private String description;

    public Transaction(LocalDate date, double amount, String description) {
        this.date = date;
        this.amount = amount;
        this.description = description;
    }

    public LocalDate getDate() {
        return date;
    }

    public double getAmount() {
        return amount;
    }

    public String getDescription() {
        return description;
    }

    @Override
    public String toString() {
        return "Transaction{" +
                "date=" + date +
                ", amount=" + amount +
                ", description='" + description + '\'' +
                '}';
    }
}

class TransactionParser {

    public List<Transaction> parse(String filePath) throws IOException {
        List<Transaction> transactions = new ArrayList<>();
        BufferedReader reader = new BufferedReader(new FileReader(filePath));
        String line;
        reader.readLine(); // Skip header line
        while ((line = reader.readLine()) != null) {
            String[] parts = line.split(",");
            LocalDate date = LocalDate.parse(parts[0]);
            double amount = Double.parseDouble(parts[1]);
            String description = parts[2];
            transactions.add(new Transaction(date, amount, description));
        }
        reader.close();
        return transactions;
    }
}


class TransactionAnalyzer {

    public double calculateTotal(List<Transaction> transactions, String type) {
        return transactions.stream()
                .filter(t -> (type.equals("income") && t.getAmount() > 0) || 
                             (type.equals("expense") && t.getAmount() < 0))
                .mapToDouble(Transaction::getAmount)
                .sum();
    }

    public Transaction findLargestTransaction(List<Transaction> transactions, String type) {
        return transactions.stream()
                .filter(t -> (type.equals("income") && t.getAmount() > 0) || 
                             (type.equals("expense") && t.getAmount() < 0))
                .max(Comparator.comparingDouble(t -> Math.abs(t.getAmount())))
                .orElse(null);
    }

    public List<Transaction> filterByKeyword(List<Transaction> transactions, String keyword) {
        return transactions.stream()
                .filter(t -> t.getDescription().toLowerCase().contains(keyword.toLowerCase()))
                .collect(Collectors.toList());
    }
}


class TransactionReport { 

    public void printSummary(List<Transaction> transactions) {
        System.out.println("Transactions Summary:");
        transactions.forEach(System.out::println);
    }
}

public class BankStatementAnalyzer {

    public static void main(String[] args) {
        String filePath = "transactions.csv";
        TransactionParser parser = new TransactionParser();
        TransactionAnalyzer analyzer = new TransactionAnalyzer();
        TransactionReport report = new TransactionReport();

        try {
            // Parse transactions from file
            List<Transaction> transactions = parser.parse(filePath);

            // Calculate totals
            double totalIncome = analyzer.calculateTotal(transactions, "income");
            double totalExpense = analyzer.calculateTotal(transactions, "expense");

            // Find largest transactions
            Transaction largestIncome = analyzer.findLargestTransaction(transactions, "income");
            Transaction largestExpense = analyzer.findLargestTransaction(transactions, "expense");

            // Filter by keyword
            List<Transaction> rentTransactions = analyzer.filterByKeyword(transactions, "Rent");

            // Print results
            System.out.println("Total Income: " + totalIncome);
            System.out.println("Total Expense: " + totalExpense);
            System.out.println("Largest Income Transaction: " + largestIncome);
            System.out.println("Largest Expense Transaction: " + largestExpense);
            System.out.println("Transactions containing 'Rent':");
            report.printSummary(rentTransactions);

        } catch (IOException e) {
            System.err.println("Error reading the file: " + e.getMessage());
        }
    }
}

# Sơ đồ UML class Transaction
![Phanttext](https://www.planttext.com/api/plantuml/png/d9F1JiCm38RlUOgefrRgNW2XQKFSs65YapYR9YiHQL8bhb10F1a77ebN8CaANKeafjqYs__dtxRozV6viWW6XquIqaYmbkuDA0ksGQ4LUIEKBXWWfrTqenkGj_uTOj3fGQ6FCZqyoXXYt3P6z47dupiqGhK-dW3BEQkcCr9DSvmgW5gEGL9MCpCXiOwKcFfr50KJB2P7M-_fjD7R5epb9evC-_Wk3qBoBU3Jv2Eq5XQlJuTQPd5h1TAz_W2zssQGtkzU8yWIfpgRHTOKNS-JljDS1w7O1apBBPuql0YQN3kYfKHkRjmTTm_Qi7EWpzoz-D9BbdJFUsrmtBdNucxeEZ3k_xPLuFsv7bqibibCNbiSZrcGp76ozJ0c4yNHQQwU5iRd_2UYMXM4hBXY_Zjz0m00__y30000)

# Explanation of SRP, Cohesion, and Coupling

1. Single Responsibility Principle (SRP)
SRP yêu cầu mỗi lớp chỉ thực hiện một trách nhiệm duy nhất. Trong thiết kế này:

+Transaction:

      +Đóng vai trò là mô hình dữ liệu, chỉ đại diện cho một giao dịch (các thuộc tính: ngày, số tiền, mô tả).
  
+TransactionParser:

      +Chỉ chịu trách nhiệm đọc và phân tích dữ liệu từ file CSV để tạo ra danh sách các đối tượng Transaction.
  
+TransactionAnalyzer:

+Chỉ tập trung vào logic phân tích, bao gồm:

      +Tính tổng thu nhập hoặc chi tiêu.
      +Tìm giao dịch lớn nhất.
      +Lọc giao dịch dựa trên từ khóa.
  
+TransactionReport:

      +Chịu trách nhiệm duy nhất là hiển thị dữ liệu giao dịch, đảm bảo code không bị rối loạn bởi logic phân tích.
  
    -> Cách áp dụng SRP: Mỗi lớp trong chương trình có nhiệm vụ rõ ràng và độc lập, giúp dễ dàng bảo trì, kiểm tra và mở rộng.


2. Cohesion
Tính gắn kết yêu cầu các thành phần trong một lớp phải tập trung thực hiện nhiệm vụ cụ thể và liên quan chặt chẽ.

+Tăng tính gắn kết:

    +Các lớp như TransactionParser, TransactionAnalyzer, và TransactionReport chỉ chứa các phương thức liên quan trực tiếp đến nhiệm vụ của chúng.
    Ví dụ:
    TransactionParser chỉ liên quan đến việc đọc file và chuyển đổi dữ liệu thành danh sách giao dịch.
    TransactionAnalyzer chứa tất cả logic tính toán và phân tích.
    TransactionReport chỉ in kết quả, không can thiệp vào logic phân tích hoặc thao tác dữ liệu.
+Lợi ích:

    Gắn kết cao giúp các lớp dễ hiểu, dễ sử dụng và tránh việc các phương thức hoặc thuộc tính không liên quan xuất hiện trong một lớp.


3. Coupling
Coupling yêu cầu giảm thiểu sự phụ thuộc giữa các lớp để tăng khả năng mở rộng và thay đổi mà không ảnh hưởng đến toàn bộ hệ thống.

+Giảm độ phụ thuộc:

    +Các lớp giao tiếp với nhau qua danh sách Transaction, không chia sẻ trực tiếp logic bên trong.
    
Ví dụ:

    +TransactionParser chỉ trả về danh sách Transaction và không quan tâm cách danh sách đó được phân tích hoặc hiển thị.
    +TransactionAnalyzer và TransactionReport hoạt động độc lập, chỉ nhận dữ liệu đầu vào cần thiết.
    
    +Các phương thức static (static) trong TransactionParser và TransactionAnalyzer đảm bảo không cần phải khởi tạo đối tượng, giảm sự phụ thuộc lẫn nhau giữa các lớp.

+Lợi ích:

    +Dễ dàng thay thế hoặc sửa đổi logic của một lớp mà không ảnh hưởng đến các lớp khác.
    +Ví dụ: Nếu cần thay đổi nguồn dữ liệu (từ CSV sang JSON), chỉ cần cập nhật TransactionParser.

