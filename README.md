# Twig Cheat Sheet

## Delimiters

- For printing variables
    - `{{ <VARIABLE> }}`
- For executing statements
    - `{% <STATEMENT> %}`

## Variables

### Accessing

- Use dot notation or subscript syntax to access attributes of a variable
    - `foo.bar`
    - `foo['bar']`
    - Attributes with special characters: use attribute function
        - `attribute(foo, 'data-foo')`

### Setting

Use set tag

`{% set <ASSIGNMENT STATEMENT> %}`

ie. `{% set foo = 'foo' %}`

### Filtering

- Use the pipeline to filter variables
    - `{{ name | title }}`
    - Filters can be chained
    - See [https://twig.symfony.com/doc/2.x/](https://twig.symfony.com/doc/2.x/) for a list of filters

## Functions

See [https://twig.symfony.com/doc/2.x/](https://twig.symfony.com/doc/2.x/) for a list of functions

*Named arguments may be used*

## Conditionals

If / else / else if structure
```
{% if <IF STATEMENT> %}
    <CODE>
{% elseif <IF STATEMENT> %}
    <CODE>
{% else %}
    <CODE>
{% endif %}
```

### Comparisons

- `==`
- `!=`
- `<`
- `>`
- `>=`
- `<=`
- `starts with`
- `ends with`
- `matches` (uses regular expressions)

## Loops

For loop structure
```
{% for <FOR STATEMENT> %}
    <CODE>
{% endfor %}
```
## Comments

Use `{# <COMMENT> #}` to write comments

## Including templates

- Use `include('<TEMPLATE PATH>')` to include a template
- Included templates have access to the same context as the template that includes them (ie. variables)

## Template inheritance

- Can define a skeleton template and can use blocks which child templates can override

### Parent template

- Use block tag to allow a child to override the block
    - ```
        {% block <BLOCK NAME> %}
            <OPTIONAL CODE>
        {% endblock %}

### Child template

- Use extends tag to override parent
    - `{% extends "<PARENT TEMPLATE PATH>" %}`
- Use block tag to override parent block
    - ```
        {% block <BLOCK NAME (same as parent to override)> %}
            <CODE>
        {% endblock %}
- Use the parent function to copy parent block's contents to child blocks contents
    - `{{ parent() }}`

## Literals

- Strings (in double / single quotes)
- Numbers
    - Integers
    - Floats
- Arrays (in brackets `[]` separated by commas `,`)
- Hashes (in curly braces `{}` separated by commas `,` with keys and values separated by colons `:`)
- Booleans
    - true
    - false
- Null (`null`)

*Note that arrays and hashes can be nested*

## Math

Math can be done in `{{ <MATH EXPRESSION> }}` braces

## Logic

Operators
- `and`
- `or`
- `not`

## Operators

### Containment

- `in`
    - Returns true if left operand is in right
    - Can use `not` for opposite effect

### String interpolation

Allows expression in DOUBLE-QUOTED strings (`#{ <EXPRESSION> }`)

ie. `{{ "foo #{bar} baz" }}`
