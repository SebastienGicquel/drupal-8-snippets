## Disable label, custom fiel machine name : field_prenom 
```php
$form['name']['#title_display'] = 'invisible';
$form['field_prenom']['widget'][0]['value']['#title_display'] = 'invisible';
```
