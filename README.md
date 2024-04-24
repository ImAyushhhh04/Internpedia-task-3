# Internpedia-task-3
# Online Examination code:
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

// User class representing a user in the system
class User {
    private String username;
    private String password;
    private String fullName;

    public User(String username, String password, String fullName) {
        this.username = username;
        this.password = password;
        this.fullName = fullName;
    }

    public String getUsername() {
        return username;
    }

    public String getPassword() {
        return password;
    }

    public String getFullName() {
        return fullName;
    }

    public void setPassword(String newPassword) {
        this.password = newPassword;
    }

    public void setFullName(String newFullName) {
        this.fullName = newFullName;
    }
}

// Authentication class to handle login and logout
class Authentication {
    private Map<String, User> users;

    public Authentication() {
        users = new HashMap<>();
    }

    public void addUser(String username, String password, String fullName) {
        User user = new User(username, password, fullName);
        users.put(username, user);
    }

    public boolean login(String username, String password) {
        if (users.containsKey(username)) {
            User user = users.get(username);
            if (user.getPassword().equals(password)) {
                System.out.println("Login successful. Welcome, " + user.getFullName() + "!");
                return true;
            }
        }
        System.out.println("Invalid username or password. Please try again.");
        return false;
    }

    public void logout() {
        System.out.println("Logout successful.");
    }
}

// Main class to simulate the application flow
public class Application {
    private static Authentication authentication = new Authentication();
    private static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        authentication.addUser("Ayush", "Ayush04", "Ayush shrihari Bothe");
        authentication.addUser("Sainath", "sai09", "Sainath shantabai Amune");

        while (true) {
            System.out.println("\nWelcome Ayush to the Application!");
            System.out.println("1. Login");
            System.out.println("2. Exit");

            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    login();
                    break;
                case 2:
                    System.out.println("getout,tata,Goodbye!");
                    System.exit(0);
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }

    private static void login() {
        System.out.print("Enter username: ");
        String username = scanner.next();
        System.out.print("Enter password: ");
        String password = scanner.next();
        authentication.login(username, password);
        if (authentication.login(username, password)) {
            // Proceed to other functionalities after successful login
            System.out.println("Other options are also here Ayush Bothe pls try this!!");
            // Simulate logout
            authentication.logout();
        }
    }
}
