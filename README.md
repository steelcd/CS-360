# CS-360
## Mobile Architecture and Programming

- Briefly summarize the requirements and goals of the app you developed. What user needs was this app designed to address?

StashWise is a lightweight inventory tracking app that helps homeowners, hobbyists and small business owners keep track of import items and retrieve alerts on items that are out of stock. The free version includes local storage of inventory, while the pro version stores the inventory on the cloud and multi-user access. This is an attractive solution for users with its streamlined app design and doesn’t require a desktop computer and unstructured excel sheets.

- What screens and features were necessary to support user needs and produce a user-centered UI for the app? How did your UI designs keep users in mind? Why were your designs successful?

Like most apps, StashWise requires authorization to use the application. A login screen allows the user to either create or login into an existing account. The application doesn’t store the password but follows best practice for sorting a hashed/salted value.
After successful login, the user is presented with an inventory overview screen which displays a table of their inventory, location and quantity. Users can delete unneeded items directly from this screen. Menu options from this screen include add a new item, updating inventory quantities and adding SMS low stock notifications.
Instead of including a screen where a user would need to type in an item name to update, the screen includes an update qty button. The user can them simply tap on the intended row to update. This is a good function where users may have few items to track. For the future, it would be helpful to also include an option to type in and have some type auto complete.
The SMS screen is simple, when clicking on the SMS notification button, a function is ran that checks if the app has permissions for SMS. If not, permission is requested. Once permission is granted, the screen displays allowing a user to add a phone number. To send SMS, it’s a follow-on action from committing an inventory update. If permission is granted and the stock is zero, the app checks for SMS numbers added to the DB; if it finds any, an SMS message is sent. A toast message is displayed indicating when a low-stock notification is sent and the number of recipients it was sent to.

This design keeps the user in mind by presenting a common theme and colors and only having the functions needed for the user. Having a simple interface and clear call to action buttons means that most users can adopt the application with little to no training.

- How did you approach the process of coding your app? What techniques or strategies did you use? How could those techniques or strategies be applied in the future?

The user requirements were determined first. Following this, an application wireframe was developed to meet those requirements. From there, the infrastructure and data design was completed. This is required since the code will create the data storage upon loading and is developed around interacting with the data.
Once this was done, pseudocode for the controller classes were created to act as a guide for completing the code.

- How did you test to ensure your code was functional? Why is this process important, and what did it reveal?

During development, it’s important to understand how the user should interact with the program but also understand all the ways they can interact with it. With knowing the different situations or cases that may happen, the developer can account for these during development, cutting down on code changes because of QA testing.
There are multiple places in the code that need to have error handling included: the controller but also the model. By including error handling or user feedback for incorrect/required values, errors are stopped before the controller code can even execute.

- Consider the full app design and development process from initial planning to finalization. Where did you have to innovate to overcome a challenge?

I wasn’t sure of the best interface for editing the item quantities, specifically for how the user would select the item. Since this application is geared towards homeowners and hobbyists, there likely aren’t going to be significant number of records. To keep the first app iteration simple, I found that a click call back could be created for each table row that was dynamically added. A button on the screen flips a global variable to allow editing. When the variable is true and the user clicks on the row, it takes them to a view for editing that record.

- In what specific component of your mobile app were you particularly successful in demonstrating your knowledge, skills, and experience?

User accounts are very critical for security. To handle user creation and login, I created a user class. This class not only stores the username and password entered by the user but includes further functionality for authenticating or creating a user. To authenticate the user, the class queries the user database for the hashed password and salt. The salt value is used to hash the user provided password and the class checks to see if it matches. For creating a user, the class generates a random salt, hashes the password and stores the username, hashed password and salt.
