# Meal-Planner-WebApp

1.)	Download and follow the displayed instructions to install XAMPP application (to host the project by local server).  
2.)	**Copy paste the newproject folder in this XAMPP path: C:\xampp\htdocs\...  
3.)	Start MySQL and Apache from XAMPP control panel.  
4.)	Create a new database namely “recipe_app” from “http://localhost/phpmyadmin/” (server admin).  

5.)	Create “comments”, “meal_plans”, “preferences”, “recipes”, “shopping_list”, and “user” tables under the database. To create the tables:
a.	Select “recipe_app” database.
b.	Click on the SQL tab to run SQL queries.
c.	Run the following SQL queries to create the tables:
i.	Users table
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    password VARCHAR(255) NOT NULL,
    email VARCHAR(100) NOT NULL,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
ii.	Recipes table
CREATE TABLE recipes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    instructions TEXT NOT NULL,
    prep_time INT NOT NULL,
    cook_time INT NOT NULL,
    nutritional_info TEXT,
    ingredients TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
iii.	Comments table
CREATE TABLE comments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    recipe_id INT NOT NULL,
    user_id INT NOT NULL,
    comment TEXT NOT NULL,
    rating INT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (recipe_id) REFERENCES recipes(id) ON DELETE CASCADE,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);
iv.	Shopping_list table
CREATE TABLE shopping_list (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    item VARCHAR(255) NOT NULL,
    category VARCHAR(50) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);
v.	Meal_plans table
CREATE TABLE meal_plans (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    recipe_id INT NOT NULL,
    date DATE NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
    FOREIGN KEY (recipe_id) REFERENCES recipes(id) ON DELETE CASCADE
) ENGINE=InnoDB;
vi.	Preferences table
CREATE TABLE IF NOT EXISTS preferences (
    user_id INT PRIMARY KEY,
    dietary_preferences VARCHAR(255) NOT NULL,
    allergies VARCHAR(255) NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
) ENGINE=InnoDB;  
   
6.)	Once the setup is done, Visit the website with “http://localhost/newproject/ “ from any browser to launch the project.
 

