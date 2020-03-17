## JSX rules:
1. All tags must be closed
    1. Either self close <img />
    2. Open and close <div></div>
2. Follow proper html tree structure
3. The return should be 1 complete html element(it can have nested elements)
4. No HTML comments!
    1. [link](https://web.compass.lighthouselabs.ca/days/w06e/activities/985) for how the error messages would look like

## short-circuit JS in React
* true && expression always evaluates to expression
* false && expression always evaluates to false
* <strong>It is important to understand the "logical &&" syntax used inline with JSX. The if() {} block is not valid within a JSX declaration and it will produce an error.</strong>
* if the conditional has more than 1 html element you need to use fragments, see below:

There are three ways to access the Fragment, which is a component type provided by React.
1. `import React, { Fragment } from 'react'` would be required for the above example
2. `<React.Fragment></React.Fragment>` would use the already imported React reference
3. `<>...</>` is the shorthand for a Fragment

## hooks
Hooks have to be initialized inside of the body of a React Component. You can’t initialize them outside of the body or inside of a function.
