Style Guide JavaScript
======================

General guidelines
------------------

* Investigate third-party code like jQuery plugins before building your own - balance the cost
    of integration and bloat versus benefits of standardization and code consistency
* Avoid embedding JavaScript code in HTML; use external libraries instead
* Minify, obfuscate, and gzip JavaScript and CSS before go-live (e.g. Uglify, Closure Compiler,
    YUI Compressor)

Code layout and comments
------------------------

### Use white space to help comprehension

* Indent two spaces per code level
* Use spaces, not tabs to indent as there is not a standard for the placement of tabs stops
* Limit code and comment lines to a maximum of 78 characters
* Follow a function with no space and then its opening left parenthesis, (.
* Follow a keyword with a single space and then its opening left parenthesis, (.
* Each semicolon ; in the control part of a for statement should be followed with a space.
* Align like elements vertically to aid comprehension, within reason
* Prefer single quotes over double quotes for string delimiters

### Organize your code in paragraphs

* Organize your code in logical paragraphs and place blank lines between each
* Each line should contain at most one statement or assignment although we do allow
    multiple variable declarations per line
* Place white space between operators and variables so that variables are easier to spot
* Place white space after every comma
* Align like operators within paragraphs
* Indent comments the same amount as the code they explain
* Place a semicolon at the end of every statement
* Place braces around all statements in a control structure. Control structures include
    for, if, and while constructs, among others.

### Break lines consistently

* Break lines before operators as one can easily review all operators in the left column.
* Indent subsequent lines of the statement one level e.g. two spaces in our case.
* Break lines after commas separators.
* If there is no closing bracket or parenthesis, place it on its own line. This clearly
    indicates the conclusion of the statement without forcing the reader to scan horizontally
    for the semicolon.

### Use K&R style bracketing

* Place the opening parenthesis, brace or bracket at the end of the opening line
* Indent the code inside the delimiters (parenthesis, brace, or bracket) one level - e.g. two spaces
* Place the closing parenthesis, brace or bracket on its own line with the same indentation
as the opening line

### Comment strategically

* Align comments to the same level as the code they explain
* Comment frugally. Prefer to comment at the paragraph level.
* Non-trivial functions should explain the purpose of the function, what arguments it
    uses, what settings it uses, what it returns, and any exceptions it throws.
* If you disable code, explain why with a comment of the following format:
    // TODO <YYYY-MM-DD> <username> - <comment>.
* Use JSDoc to document functions, classes, objects etc.

### Examples of API documentation for a function

``` JavaScript
/**
 * Reads all books from server by title and author.
 *
 * @public
 * @param  {string} strTitle  - string of the title of the book
 * @param  {string} strAuthor - string of the author of the book
 * @return {array}            - array of books found by title and author
 */
function readBooksByTitleAndAuthor(strTitle, strAuthor) {
    // read books from server via AJAX
    return arrBooks;
}
```

or

``` JavaScript
/**
 * Converts books (text) into objects.
 *
 * @private
 * @param  {array} arrBooksSource - array of texts of books source
 * @return {array} arrBooksResult - array of book objects result
 */
function _makeBookObjectsFromBooksList(arrBooksSource) {
}
```

Variable names
--------------

### Use common characters

* Use only a-z, A-Z, 0-9, underscore, or $
* Do not begin a variable name with a number

### Communicate variable scope

* Use camelCase when the variable is full-module scope (i.e. it can be accessed anywhere
    in a module namespace).
* Use under_scores when the variable is not full-module scope (i.e. variables local to a
    function within a module namespace).
* Make sure all module scope variables have at least two syllables so that the scope is
    clear. For example, instead of using a variable called config we can use the more
    descriptive and obviously module-scoped configMap.
    Objects typically have a concrete "real world" analog and we name them accordingly:
* An object variable name should be a noun followed by an optional modifier, e.g.
    employee or receipt.
* Make sure a module-scoped object variable name has two syllables or more so the
    scope is clear, e.g. storeEmployee or salesReceipt.
* Prefix jQuery objects with a $. This is a pretty common convention these days, and
    jQuery objects (or collections as they are sometimes called) are quite prevalent in SPAs.

### Variable name conventions

#### declaration and assignment

* Use `{}` or `[]` instead of `new Object()` or `new Array()` to create a new object, map, or array.
* Use utilities to copy objects and arrays. See `jQuery.extend()`.
* Explicitly declare all variables first in the functional scope using a single var keyword.
* Use named arguments whenever requiring 3 or more arguments in a function, as
    positional arguments are easy to forget, and are not self-documenting.
    Alternatively use an object with fields as arguments.
* Use one line per variable assignment. Order alphabetically group logically
* More than one declaration may be placed on a single line.

#### Common conventions

* `_...`. `__...`, ...: private variable indication (`_isDone`)

#### Boolean type

* `bool...`: boolean type (`boolDone`, `boolCreated`)
* `b...`: boolean type (`bDone`, `bCreated`)
* `be...`: boolean type (`beDone`, `beCreated`)
* `is...`: state (`isDone`, `isCreated`)
* `has...`: inclusion (`hasMembers`, `hasClients`)

#### String type

* `str...`: general, single-line string type (`strType`, `strAddress`)
* `text...`: multiline string type (`textMessage`, `textInfo`)
* `id...`: string identifiers (`idUser`, `idMember`)
* `html...`: HTML strings (`htmlForm`, `htmlElement`)

### Number type

* `num...`: general number (integer or decimal) type (`numPlayers`, `numCounter`)
* `index...`, `i`: integer index type (`indexUsers`, `iUsers`)
* `int...`: general integer type (`intSizeX`, `intOffsetX`)
* `dec...`, `flt...`: general decimal/floating number type (`decRatio`, `fltOpacity`)
* `i`, `j`, `k`: integer index counter variables

#### Array type

* `arr...`: general array type (`arrUsers`, `arrDifferentTypes`)
* `arr...<type>`: array of types `<type>` (`arrObjUsers`, `arrNumCounters`)
* `list...`: array type for array of strings (`listNames`, `listEmails`)
* `arrOr...<type>`: array type for multiple, possible types (`arrOrBoolUsers`, `arrOrStrUsers`)

#### Object type

* `date...`: JavaScript date object for dates (`dateCreatedAt`, `dateNow`)
* `time...`: JavaScript date object for times (`timeCreatedAt`, `timeNow`)
* `dateTime...`: JavaScript date object for both dates and times (`dateTimeCreatedAt`, `dateTimeNow`)
* `regex...`, `pattern`: regular expression object (`regexName`, `patternEmail`)
* `filter...`: regular expression object for filtering purpose (`filterAge`, `filterPassword`)

#### Set and map types

* `map...`: general map type (`mapEmployees`)
* `set...`: general set type (`setNumbers`)

#### Unformatted and constant objects

* To indicate that an object contains unformatted properties (including sub-objects), add
    the `_u` postfix to the variable's name.

    Example:

    ``` JavaScript
    var objUser_u = {
        username : 'jonDoe',
        firstName: 'Jon',
        lastName : 'Doe',
        email    : 'jondoe@email.org'
    };
    ```

    None of the object's properties has a prefix to express its type. Usually data from servers
    and unformatted APIs lack in prefixes for which this notation is useful.

* To indicate that an object contains constant values, add
    the `_c` postfix to the variable's name.

    Example:

    ``` JavaScript
    var objUser_c = {
        USERNAME  : 'jonDoe',
        FIRST_NAME: 'Jon',
        LAST_NAME : 'Doe',
        EMAIL     : 'jondoe@email.org'
    };
    ```

    In this object there should only be string and number properties.

#### Special naming conventions for variables

* In node/express use `req` for request and `res` for response objects.

### Function name conventions

#### Common conventions

* Use functions to provide scope, the JavaScript `let` statement has questionable value.
* Use the factory pattern for object constructors, as it better illustrates how JavaScript
    objects actually work, is very fast, and can be used to provide class-like capabilities.
* Avoid pseudo classical object constructors - those that take a new keyword. If you must
    keep such a constructor, capitalize its first letter.
* When a function is to be invoked immediately, wrap the function in parenthesis so that
    it is clear that the value being produced is the result of the function.
* Function variable names should always start with a verb followed by a noun.
* Module-scoped functions should always have two syllables or more so the scope is
    clear, e.g. `getRecord` or `emptyCacheMap`.

#### Specific conventions

* `_...`, `__...`, ...: private function indication (`_createUser`)
* `fn...`: generic function or callback indicator (`fnSync`)
* `cb`, `callback`: callback naming convention
* `next`: next (callback) function for Node.js / Express middleware
* `curry...`, `c...`: with a function as return value (currying) (`cCompile` i.e. returns the linking function)

#### Conventions for external sources

* `create...`, `make...`: create a new object in an external source (`createUser`)
* `read...`, `fetch...`: fetch / read data from a external source (`readUsers`)
* `update...`: update data in a external source (`updateUser`)
* `patch...`: patch data in a external source (`patchUserName`)
* `delete...`: delete data in an external source (`deleteUser`)

### Conventions for internal sources

* `get...`: get data from a local source (`getUserList`)
* `save...`: save an existing local source (`saveUserList`)
    (to synchronize two different local sources if necessary)
* `set...`: set data in an existing local source (`setNameInUserList`)
* `remove...`: remove existing local source or data from existing local source
    (`removeUser`, `removeEmailFromUser`)
* `insert...`, `push...`: insert element in array or object
    (`insertUserInUserList`, `pushClientIntoClientList`)
* `remove`, `pull...`: remove element from array or object
    (`removeUserFromUserList`, `pullClientFromClientList`)
* `empty`: remove all elements from array or object
    (`emptyUsersInUserList`)

Namespaces and file layout
--------------------------

### Namespace basics

* Claim a single, short name (2-4 letters) for your application namespace, e.g. spa.
* Subdivide the namespace per responsibility, e.g. spa.data, spa.model, spa.shell, etc.

### JavaScript files

* Include third-party JavaScript files first in our HTML so their functions may be
    evaluated and made ready to our application.
* Include our JavaScript files in order of namespace. You cannot load namespace
    spa.shell, for example, if the root namespace, spa, has not yet been loaded.
* Give all JavaScript files a .js suffix
* Store all Static JavaScript files under a directory called js.
* Use the template to start any JavaScript module file.
* Name JavaScript files according to the namespace they provide, one namespace per
    file. Examples: `spa.js`, `spa-shell.js`, `spa-chat.js`

### CSS files

* A CSS file should be created for each JavaScript file that generates HTML. Examples:
    * `spa.css // spa.*` namespace
    * `spa-shell.css // spa-shell.*` namespace
    * `spa-slider.css // spa-slider.*` namespace
* Give all CSS files a .css suffix
* Store all CSS files under a directory called css
* CSS id's and class names should be prefixed according to the name of the module they
    support. Examples:
    * `spa.css` defines `#spa`, `.spa-x-clearall` etc.
    * `spa.shell.css` defines `#spa-shellheader`, `#spa-shell-footer`, `.spa-shell-main` etc.
* Use application prefix for all classes and id's to avoid unintended interaction with
    third-party modules
* Use `<namespace>-x-<descriptor>` for state-indicator and other shared class names.
    Examples might include `spa-x-select` and `spa-x-disabled` and defined in the spa.css file.