It's easy to enable variables and conditional text in an MkDocs + Material ecosystem.

And you don’t really need to know Python.

This is in our mkdocs.yml file, which are our defined variables (anonymized):

plugins:
extra:
  content-customer: false
  platformname: "value1"
  productname1: "value2"
  featurename: "value3"
  productname: "value4"

plugins:
   macros:
     include_dir: docs/includes
Then, in your .md Markdown file, to substitute a variable value, just name it inside double curly braces:
{{ featurename }}
{{  productname }}
To do conditional text for only content-customer (this is the name of one of our customers in our implementation):

{% if contentcustomer %}
some content only for special customer eyes
{% endif %}
If you want to only show something for other customers, use “not”:

{% if not contentcustomer %}  
some content only for other customer eyes
{% endif %}To do an if/then/else statement:
{% if contentcustomer %}
some content only for special customer eyes
{% else %}
some content only for other customers eyes
{% endif %}
We also use the macros plugin for includes, as we found that the snippets plugins didn’t work with the variables, but includes are the same thing and they do.

You place your 'include' file (a standard .md file)  in the place you defined in your mkdocs.yml file. In our case, it's in docs/includes. Then in the file where you want to include the contents of that other file:

{% include 'filename.md' %}