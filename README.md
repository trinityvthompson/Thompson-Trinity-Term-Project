### 1. **What is your project idea about?**

My project idea is a restaurant ordering system designed for a small restaurant. The system allows customers to place orders for either a veggie burger or a cheeseburger through a simple menu-driven interface. The program manages the inventory of ingredients used in these burgers, tracks stock levels, and updates inventory as orders are processed. The system uses a Queue to manage orders and processes them in First-In-First-Out (FIFO) order. Additionally, it supports inventory checks and displays the current stock of ingredients, and sorts them based on quantity in descending order using the merge sort algorithm.

### 2. **If you use any datasets, describe the dataset and provide how one can access and download it.**

This project does not use any external datasets. The inventory and burger details are defined directly in the program through hardcoded values, such as ingredient names, quantities, and prices.

### 3. **Describe your design for main packages, classes, methods, functions, and iterations between them.**

Classes and methods:

- **Ingredient Class**: Represents an ingredient in the restaurant’s inventory. It includes properties like name, quantity, and price.
  - __init__(self, name, quantity, price): Initializes an ingredient with a name, quantity, and price.
  - __str__(self): Returns a string representation of the ingredient.
  
- **Inventory Class**: Manages the ingredients used in the restaurant. It allows adding ingredients, updating stock, checking inventory, and sorting ingredients based on stock.
  - add_ingredient(self, ingredient): Adds an ingredient to the inventory.
  - update_inventory(self, ingredient_name, quantity_used): Reduces the stock of a given ingredient.
  - check_inventory(self): Displays all ingredients in the inventory.
  - merge_sort(self, ingredients_list): Sorts the ingredients list by stock quantity in descending order using the merge sort algorithm.
  - sort_inventory(self): Sorts and displays the inventory by stock quantity.

- **Order Class**: Represents a customer’s order and includes a method for processing that order (updating inventory).
  - create_order_items(self, burger_type): Based on the burger type (veggie_burger or cheeseburger), it returns the required ingredients.
  - process_order(self, inventory): Processes the order by updating the inventory with the required ingredients.

- ** Queue Class**: Manages the orders placed by customers in a FIFO manner. This ensures that the first order placed is the first one processed.
  - add_order(self, order): Adds an order to the queue.
  - process_next_order(self, inventory): Processes the next order in the queue and updates inventory accordingly.

- **Restaurant Class**: The main class managing the restaurant operations, including placing orders, checking inventory, and sorting it.
  - add_ingredient(self, name, quantity, price): Adds ingredients to the inventory.
  - show_inventory(self): Displays the current inventory.
  - sort_inventory(self): Sorts the inventory by stock and displays it.
  - place_order(self, order_id, burger_type): Places an order in the queue.

### 4. **Describe any libraries that you use.**

I did not use any external libraries, as the program uses only built-in Python functions. The merge_sort algorithm is implemented manually within the Inventory class.


### 5. **Design some Test cases that can test the correctness of your software.**

Here are some test cases that will verify different functionalities of the system:

1. **Test Case 1: Place an Order**
   - **Input**: Customer chooses the "Veggie Burger" (1) from the menu.
   - **Expected Outcome**: The system should process the order, reduce the inventory of Lettuce, Tomato, Veggie Patty, and Bun by 1 unit each, and place the order in the queue.
   
2. **Test Case 2: Inventory Check**
   - **Input**: Customer chooses the "Check Inventory" option.
   - **Expected Outcome**: The system should display the current stock of all ingredients.

3. **Test Case 3: Show Sorted Inventory**
   - **Input**: Customer chooses the "Show Sorted Inventory" option.
   - **Expected Outcome**: The system should display the inventory sorted by quantity in descending order (highest quantity first).

4. **Test Case 4: Process Orders**
   - **Input**: Customer places two orders (one Veggie Burger, one Cheeseburger). Then, the "Process Orders" option is chosen.
   - **Expected Outcome**: The system should process both orders in FIFO order, updating the stock correctly, and display updated inventory.

5. **Test Case 5: Order Processing with Low Stock**
   - **Input**: Place multiple orders until the stock of an ingredient (e.g., "Lettuce") is low.
   - **Expected Outcome**: The system should alert the user when an ingredient is running low and indicate that it should be reordered.

### 6. **What is your current expectations of your software? For example, do you expect that it works well? What are the expected weaknesses?**

**Expectations**:
- The software should work well for simulating a simple restaurant ordering system.
- Orders should be processed correctly, inventory updated in real-time, and customers should be able to view current stock levels and place orders in a user-friendly manner.
- Sorting the inventory with the merge sort should function correctly, even with a small set of data.

**Expected Weaknesses**:
- Currently, there are no checks for invalid orders (e.g., trying to place an order with ingredients that are out of stock). This could be an issue when stock levels reach zero.
- The system currently only supports two types of burgers. In a real-world scenario, a restaurant would likely have a more complex menu.
- The system doesn't save data. If the program is restarted, the inventory and orders are reset. In a real-world scenario, this would need to be stored in a database or a file.
