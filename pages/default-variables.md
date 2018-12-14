---
title: Useful Variables
layout: default
---

{% include back.html %}

## DEBUG_MODE
*Name:* `DEBUG_MODE`

This is an alias for the variable `Debug Mode` which just doesn't fit the naming conventions we use in GTM. Alaising this variable makes your tags look cleaner.

### Configuration
Create a `Custom Variable` in tag manager, name it `DEBUG_MODE` and set its type to `Debug Mode` which is in `Container Data`

### Usage
{% raw %}
`{{DEBUG_MODE}}` will return `true` if you're Previewing your workspace changes in GTM.
{% endraw %}

### Example in Tag
{% raw %}
```javascript
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
```javascript
function(){
  return 'https://code.jquery.com/jquery-3.3.1.min.js';
}
```
{% endraw %}

### Usage (tag)
Throw it into a [Load Script](#load_script) function variable.

{% raw %}
```javascript
// Loads jQuery from your CDN Link
{{LOAD_SCRIPT}}({{JQUERY_CDN}})
```
{% endraw %}

# Lookup Tables
Lookup Tables are great for Environment based configuration.




# Function Variables
GTM Custom Javascript Variables are a function that returns a `whatever`.  
Here's some that make life easier.

## CONSOLE_LOG
This is a really useful one: console.log only if you're in Preview Mode.

It checks `DEBUG_MODE` and if `true` it passes on the input to `console.log`. You can also override the other console methods if you like.
If you're really brave you can hook into `console` and replace all the methods within a `closure`, up to you, it's dangerous but useful.

### Configuration
- Create a `Custom Variable` in tag manager  
- Name it `CONSOLE_LOG`  
- Set its Type to `Custom Javascript`  
- Paste this in there.  

{% raw %}
```javascript
function() {
  return function() {
      var args = arguments;
        if({{DEBUG_MODE}}) console.log.apply(console, arguments);
    }
}
```
{% endraw %}

### Usage
In another function variable, or tag.

{% raw %}
```javascript
{{CONSOLE_LOG}}('Loading:', someJsVariable);
```
{% endraw %}

## LOAD_SCRIPT
This is a really useful one with some caveats. The biggest issue with loading stuff through GTM is timing, your script must load before you expect to use it.

### Configuration
- Create a `Custom Variable` in tag manager  
- Name it `LOAD_SCRIPT`  
- Set its Type to `Custom Javascript`  
- Paste this in there.  

*todo:* revise to ensure usage makes sense and works.
{% raw %}
```javascript
function(){
  return function(scriptPath){
      {{CONSOLE_LOG}}('Loading: ', scriptPath, loaded);

      var el = document.createElement('script');
      el.src = scriptPath;
      el.async = 'true';
      el.addEventListener('load', function() {
        {{CONSOLE_LOG}}('Loaded: ', scriptPath);
        loaded();
      });
      document.head.appendChild(el);

    return el;
    }
}
```
{% endraw %}

### Usage
In a tag:

{% raw %}
```javascript
// Load a JS file from somewhere
{{LOAD_SCRIPT}}('Path/to/your/script.js', function(){
  // You're done loading here, continue.
});
```
{% endraw %}







*todo:* remove this, it's for the lazy (James).
{% raw %}
```javascript

```
{% endraw %}
