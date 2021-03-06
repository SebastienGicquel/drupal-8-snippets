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
## Include a module template into an other module template
```twig
{% include 'modules/Y/templates/twig-of-module-Y.html.twig' %}
```
## GET IMAGE/video URL FROM MEDIA FIELD IN TWIG

#Solution 1 : preprocess function
```php
function mytheme_preprocess_node(&$variables) {
 
  /** @var \Drupal\node\NodeInterface $node */
  $node = $variables['node'];
 
  $image_field = $node->get('field_background_image');
  if (!$image_field->isEmpty()) {
    $uri = $image_field->entity->get('field_media_image')->entity->uri->value;
    $variables['background_image_url'] = file_create_url($uri);
  }
}
```
#in  node template
```twig
{{ background_image_url }}
```

#Solution 2 : in twig template directly
```twig
{% if node.field_background_image is not empty %}
  {{ file_url(node.field_background_image.entity.field_media_image.entity.fileuri) }}
{% endif %}
```

## Access A Referenced Node's Fields - Field Level Templating
source : https://drupal.stackexchange.com/questions/233977/access-a-referenced-nodes-fields-field-level-templating
```twig
{% for item in element['#items'] %}

    <div class="slide">

        {{ item.entity.title.value }}

        {{ item.entity.field_lead.value }}
        
         {{ item.entity.field_image_page_liste.0.entity.uri.value }}

    </div>

{% endfor %}
```
#example with image in node :
```twig
{{ content.field_reference_content}}
```

and in field--node--field-reference-content.html.twig
```twig
{% for item in element['#items'] %}

    <div class="slide">

        {{ item.entity.title.value }}

        {{ item.entity.field_lead.value }}
        
         {{ item.entity.field_image_page_liste.0.entity.uri.value }}

    </div>

{% endfor %}
```
