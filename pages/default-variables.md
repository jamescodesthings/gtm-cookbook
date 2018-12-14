# Useful Variables
These are useful when developing complex things in GTM.

## Debug Mode
*Name:* `DEBUG_MODE`

This is an alias for the variable `Debug Mode` which just doesn't fit the naming conventions we use in GTM. Alaising this variable makes your tags look cleaner.

### Configuration
Create a `Custom Variable` in tag manager, name it `DEBUG_MODE` and set its type to `Debug Mode` which is in `Container Data`

### Usage
{% raw %}
`{{DEBUG_MODE}}` will return true if you're Previewing your workspace changes in GTM.
{% endraw %}

### Example in Tag
{% raw %}
```

  if({{DEBUG_MODE}}) {
    // Do something only if you're Previewing your Workspace Changes
  }
 
```
{% endraw %}

# Function Variables
GTM Custom Javascript Variables are a function that returns a `whatever`.  
Here's some that make life easier.

## Console Log
