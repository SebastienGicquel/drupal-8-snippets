## Verify a field is not empty

```twig
{% if node.field_example.value %}
{% endif %}
```

## Get URL of a link field
source : https://drupal.stackexchange.com/questions/199262/how-to-get-the-valid-url-of-a-link-field-from-within-a-twig-template#199263
```twig
{{ node.field_my_link.0.url }}
```
