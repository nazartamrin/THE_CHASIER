# THE_CHASIER


A.Aplikasi The Chasier

B.aplikasi ini berfungsi untuk menghitung jumlah total barang ataupun jasa yang digunakan

C.{ private int id; public string title { get; set; } public int quantity { get; set; } public double price { get; set; } public double subtotal { get; set; } private string type;

public Item(int id, string title, int quantity, string type, double price)
{
    this.id = id;
    this.title = title;
    this.quantity = quantity;

    this.type = type;
    this.price = price;
    this.subtotal = 0;
}
public string getTitle()
{
    return title;
}
public int getQuantity()
{
    return quantity;
}
public string getType()
{
    return type;
}
public double getPrice()
{
    return price;
}
public double getSubTotal()
{
    subtotal = price * quantity;
    return subtotal;
}  
// berfungsi untuk mendeklarisakan method item yang akan digunakan

 public partial class MainWindow : Window
 private Calculator calculator;
public MainWindow()
{
    InitializeComponent();
    calculator = new Calculator();
    listBox.ItemsSource = calculator.getListItem();
}
private void AddButton_Click(object sender, RoutedEventArgs e)
{
    string title = itemNameBox.Text;
    int quantity = int.Parse(quantityBox.Text);
    string type = typeBox.Text;
    double price = double.Parse(priceBox.Text);

    Item item = new Item(new Random().Next(), title, quantity, type, price);
    calculator.addItem(item);
    double total = calculator.getTotal();

    totalLabel.Content = String.Format("Rp. {0}", total);

    listBox.Items.Refresh();
}
} //untuk menampilkan data yang telah dimasukkan sebelumnya

private List<Item> listItem;
private double total = 0;
public Calculator()
{
    this.listItem = new List<Item>();
}
public void addItem(Item item)
{
    this.listItem.Add(item);
    this.total += item.getSubTotal();
}
public double getTotal()
{
    return total;
}
public List<Item> getListItem()
{
    return listItem;
}
// untuk melakukan perhitungan pada data yang telah dimasukkan sebelumnya

