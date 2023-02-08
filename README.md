CREATE TABLE Students (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(255),
  email VARCHAR(255),
  age INT,
  address VARCHAR(255)
);

String sql = "INSERT INTO Students (name, email, age, address) VALUES (?, ?, ?, ?)";
PreparedStatement statement = conn.prepareStatement(sql);
statement.setString(1, "John Doe");
statement.setString(2, "john.doe@example.com");
statement.setInt(3, 25);
statement.setString(4, "123 Main St");
statement.executeUpdate();

String sql = "SELECT * FROM Students";
Statement statement = conn.createStatement();
ResultSet resultSet = statement.executeQuery(sql);
while (resultSet.next()) {
  int id = resultSet.getInt("id");
  String name = resultSet.getString("name");
  String email = resultSet.getString("email");
  int age = resultSet.getInt("age");
  String address = resultSet.getString("address");
  System.out.println("id: " + id + ", name: " + name + ", email: " + email + ", age: " + age + ", address: " + address);
}

String sql = "UPDATE Students SET name = ?, email = ?, age = ?, address = ? WHERE id = ?";
PreparedStatement statement = conn.prepareStatement(sql);
statement.setString(1, "Jane Doe");
statement.setString(2, "jane.doe@example.com");
statement.setInt(3, 26);
statement.setString(4, "456 Elm St");
statement.setInt(5, 1);
statement.executeUpdate();

String sql = "DELETE FROM Students WHERE id = ?";
PreparedStatement statement = conn.prepareStatement(sql);
statement.setInt(1, 1);
statement.executeUpdate();
