When you're done [Go Back](../readme.md).

# Using Tag Manager
A quick guide on how to use the Tag Manager UI, where to go, all that jazz.

## Creating a User-Defined Variable
- Open Your Workspace in [Tag Manager](https://tagmanager.google.com)  
- Go to `Variables`  
- Scroll Down to the `User-Defined Variables` section  
- Click `New`  
- Set the `Name` Use `SNAKE_CASE_ALL_CAPS`  
- In `Variable Configuration` choose the type  
  - Most of the time you'll be using `Page Variables` > `Custom Javascript`  
  - `Debug Mode` is in `Container Data`  

### Format
You can change the output format for your variable. Most of the time you don't want to, but let's say it's `null` and you want a safe `boolean`.  
- Open the Variable  
- Edit the `Format`  
- Choose `Convert null to` and enter `false` in the input box  

