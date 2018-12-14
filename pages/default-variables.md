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

# CDNs/Constants
The easiest way to hold a constant is as the result of a `Custom Javascript` Variable.

## JQUERY_CDN
This is a cosntant that returns the CDN url for jQuery 3. You can choose to load slim/minified/a different version if you wish. It can then be used to hot-load a version of jQuery just for GTM (without muddying the global scope).

### Configuration
- Create a `Custom Variable` in tag manager  
- Name it `JQUERY_CDN`  
- Set its Type to `Custom Javascript`  
- Pick your version, get the [url from here](https://code.jquery.com/)  
- Paste this in there, see what it does, it's simple and effective.  

{% raw %}
```
function(){
  return 'https://code.jquery.com/jquery-3.3.1.min.js';
}
```
{% endraw %}

# Lookup Tables
Lookup Tables are great for Environment based configuration.




# Function Variables
GTM Custom Javascript Variables are a function that returns a `whatever`.  
Here's some that make life easier.

## Console Log
