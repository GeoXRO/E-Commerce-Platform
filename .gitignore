import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Product {
    private String id;
    private String name;
    private double price;

    public Product(String id, String name, double price) {
        this.id = id;
        this.name = name;
        this.price = price;
    }

    public String getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public double getPrice() {
        return price;
    }

    @Override
    public String toString() {
        return "ID: " + id + ", Name: " + name + ", Price: $" + price;
    }
}

class ShoppingCart {
    private List<Product> products;

    public ShoppingCart() {
        this.products = new ArrayList<>();
    }

    public void addProduct(Product product) {
        products.add(product);
    }

    public double calculateTotal() {
        double total = 0.0;
        for (Product product : products) {
            total += product.getPrice();
        }
        return total;
    }

    public void displayCart() {
        System.out.println("Shopping Cart:");
        for (Product product : products) {
            System.out.println(product);
        }
        System.out.println("Total: $" + calculateTotal());
    }

    public void clearCart() {
        products.clear();
    }
}

class Order {
    private List<Product> products;
    private double totalAmount;

    public Order(List<Product> products, double totalAmount) {
        this.products = products;
        this.totalAmount = totalAmount;
    }

    public void displayOrder() {
        System.out.println("\nOrder Summary:");
        for (Product product : products) {
            System.out.println(product);
        }
        System.out.println("Total: $" + totalAmount);
    }
}

class ECommercePlatform {
    private List<Product> availableProducts;
    private ShoppingCart cart;

    public ECommercePlatform() {
        this.availableProducts = new ArrayList<>();
        this.cart = new ShoppingCart();

        // Sample products
        availableProducts.add(new Product("P001", "Laptop", 999.99));
        availableProducts.add(new Product("P002", "Smartphone", 499.99));
        availableProducts.add(new Product("P003", "Headphones", 79.99));
    }

    public void displayAvailableProducts() {
        System.out.println("\nAvailable Products:");
        for (Product product : availableProducts) {
            System.out.println(product);
        }
    }

    public Product findProductById(String id) {
        for (Product product : availableProducts) {
            if (product.getId().equals(id)) {
                return product;
            }
        }
        return null;
    }

    public void checkout() {
        double total = cart.calculateTotal();
        if (total > 0) {
            Order order = new Order(new ArrayList<>(cart.getProducts()), total);
            order.displayOrder();
            cart.clearCart(); // Clear the cart after checkout
        } else {
            System.out.println("Your cart is empty.");
        }
    }

    public ShoppingCart getCart() {
        return cart;
    }
}

public class ECommerceApplication {
    public static void main(String[] args) {
        ECommercePlatform platform = new ECommercePlatform();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\nE-Commerce Platform");
            System.out.println("1. View Products");
            System.out.println("2. Add to Cart");
            System.out.println("3. View Cart");
            System.out.println("4. Checkout");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    platform.displayAvailableProducts();
                    break;
                case 2:
                    System.out.print("Enter Product ID to add to cart: ");
                    String productId = scanner.next();
                    Product product = platform.findProductById(productId);
                    if (product != null) {
                        platform.getCart().addProduct(product);
                        System.out.println("Product added to cart.");
                    } else {
                        System.out.println("Product not found.");
                    }
                    break;
                case 3:
                    platform.getCart().displayCart();
                    break;
                case 4:
                    platform.checkout();
                    break;
                case 5:
                    System.out.println("Exiting the platform.");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Try again.");
            }
        }
    }
}

