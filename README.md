# proposal-from-import

Proposal for Python-like import syntax extension

## Example

```javascript
from 'module' import defaultExport;
from 'module' import { export1, export2 [, ...] };
from 'module' import defaultExport, { export1, export2 [, ...] };
from 'module' import defaultExport, { export1 as alias1, export2 as alias2 [, ...] };
from 'module' import defaultExport, { export1, export2 as alias2 [, ...] };
from 'module' import defaultExport, * as moduleName;
```

## Motivation

The [specification](https://www.ecma-international.org/ecma-262/6.0/#sec-imports) says that currently proposed syntax means static code import. 
The actual module code is being imported before any code runs. 
This approach gives ample possibilities for performing static checking. That's why advanced autocompletion features are possible.
But with current syntax it's not convinient to use the autocompletion features at all. 
Until user typed a module name, a text editor cannot deduct what to complete.
So developer has to type at least `import from 'module'` and start typing brackets after `import` word then to get autocompletion running. It doesn't feel so much convenient. 
The Python-like syntax `from 'module' import ...` feels more organic way to import using autocompletion. So here comes this proposal to add support for this syntax too. The examples provided below show the main difference.

In this first example a developer has to type everything else before actually typing exported field names to get autocompletiong running.
```javascript
import { Component } from 'react';
```

In the second example a developer could just type an import statement in an organic left-to-right way. An editor will be able to identify the module name even before typing an opening bracket, so autocompletion will run when expected.
```javascript
from 'react' import { Component };
```

## So... you want this instead of import ... from?
No. The proposal offers this syntax as an alternative to `import ... from` syntax, but not as a replacement. The semantics of this syntactical extension is totally the same as of usual `import ... from`.
