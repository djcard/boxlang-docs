---
description: They gotta exist somewhere!
---

# Variable Scopes

In the BoxLang language, there are many persistence and visibility scopes that exist for variables to be placed in. These are differentiated by context: in a class, in a function, tag, thread or in a template. All BoxLang scopes are implemented as structures or hash maps of key-value name pairs. The default scope for variable storage is called `variables`. Thus you can refer variables like this in either class or Template context:

```javascript
a = "hello";
writeOutput( a );
or
writeOutput( variables.a );
```

## Persistence Scopes

Can be used in any context, used for persisting variables for a period of time.

* `session` - stored in server RAM or external storages tracked by unique web visitor
* `client` - stored in cookies, databases, or external storages (simple values only)
* `application` - stored in server RAM or external storage tracked by the running BoxLang application
* `cookie` - stored in a visitor's browser
* `server` - stored in server RAM for ANY application for that BoxLang instance
* `request` - stored in RAM for a specific user request ONLY
* `cgi` - read only scope provided by the servlet container and BoxLang
* `form` - Variables submitted via HTTP posts
* `URL` - Variables incoming via HTTP GET operations or the incoming URL

## Template Scopes (BXM)

* `variables` - The default or implicit scope where all variables are assigned to.

## Class Scopes (Class)

* `variables` - Private scope, visible internally to the class only
* `this` - Public scope, visible from the outside world
* `static` - No need for a class instance, available as a class representation

## Function Scopes

* `variables` - Has access to private variables within a Component or Page
* `this` - Has access to public variables within a Component or Page
* `local` - Function scoped variables, only exist within the function execution. Referred to as `var` scoping
* `arguments` - Incoming variables to a function

## Tag Scopes

* `attributes` - Incoming tag attributes
* `variables` - The default scope for variable assignments
* `caller` - Used within a custom tag to set or read variables within the template that called it.

## Thread Scopes

* `attributes` - Passed variables via a thread
* `thread` - A thread specific scope that can be used for storage and retrieval
* `local` - Variables local to the thread context

## **Evaluating Unscoped Variables**

If you use a variable name **without** a scope prefix, BoxLang checks the scopes in the following order to find the variable:

1. Local (function-local, UDFs and Classes only)
2. Arguments
3. Thread local (inside threads only)
4. Query (not a true scope; variables in query loops)
5. Thread
6. Variables
7. CGI
8. CFFILE
9. URL
10. Form
11. Cookie
12. Client

{% hint style="danger" %}
**IMPORTANT**: Because BoxLang must search for variables when you do not specify the scope, you can improve performance by specifying the scope for all variables. It can also help you avoid nasty lookups or unexpected results.
{% endhint %}
