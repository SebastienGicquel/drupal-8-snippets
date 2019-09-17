## Disable label
```php
// field machine name : name 
$form['name']['#title_display'] = 'invisible';
// custom field machine name : field_prenom 
$form['field_prenom']['widget'][0]['value']['#title_display'] = 'invisible';
```
## Add html placeholder attribute
```php
// field machine name : name 
$form['name']['#attributes']['placeholder'] = 'Nom';
// custom field machine name : field_prenom 
$form['field_prenom']['widget'][0]['value']['#placeholder'] = 'Prénom';
```

## Add custom CSS class to submit button
```php
$form['actions']['submit']['#button_type'] = 'cta-gradient-pink';
```
