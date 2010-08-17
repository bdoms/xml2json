Turns arbitrary XML into JSON, keeping as much of the original structure as possible while still producing valid JSON.

Dy default, input that looks like this:

<tree fruit="pear">partridge</tree>

Creates output that looks like this:

{"tree":{"fruit":"pear","text":"partridge"}}

Without attributes present, a node's value will just be its text node. So this:

<tree>partridge</tree>

Creates this:

{"tree":"partridge"}

This can also be accomplished by setting the "include-attrs" variable to false.

Child nodes are handled similarly, with the exception that if they share the same tag name, an array is created. For example:

<forest>
    <tree fruit="pear">partridge</tree>
    <tree fruit="gum">kookaburra</tree>
</forest>

Yields:

{"forest":{"tree":[{"fruit":"pear","text":"partridge"},{"fruit":"gum","text":"kookaburra"}]}}

Be sure to check any changes you make with the W3C validator: http://www.w3.org/2005/08/online_xslt/

