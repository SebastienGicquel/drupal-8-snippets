## implementing hook_form_alter in a custom module or in theme
```php
function mymodule_form_alter(&$form, &$form_state, $form_id) {
  if ($form_id = 'my_form') {
    $form['actions']['submit']['#attributes']['class'][] = 'custom-class';
  }
}
```

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

## Add classes to form elements (input, select, etc.)
```php
$form['name']['#attributes']['class'][] = 'input--hoshi';
```

## Redirect to an external URL after submitting a form
```php
use Drupal\Core\Routing\TrustedRedirectResponse;
$response = new TrustedRedirectResponse('http://google.co.in');
$form_state->setResponse($response);
```

## Send an email after submitting a form
```php
        $body = array(
            '#theme' => 'item_list',
            '#items' => [
                sprintf('Nom : %s', $nom),
                sprintf('Prénom : %s', $prenom),
                sprintf('Email : %s', $e_mail)
            ],
        );

        $langcode = \Drupal::currentUser()->getPreferredLangcode();
        $reply = NULL;
        $send = TRUE;

        $params['message'] = '<p>lorem ipsum</p>';
        $params['message'] .= render($body);
        $params['subject'] = $this->t('lorem ipsum');
        $params['options']['title'] = t('Your wonderful title');
        $params['options']['footer'] = t('Your wonderful footer');
        $params['from'] = $nom . ' ' . $prenom . '<' . $e_mail . '>';
        //envoi d'un email notification inscription
        /** @var MailManagerInterface $mailManagerService */
        $mailManagerService = \Drupal::service('plugin.manager.mail');

        $mailManagerService->mail('inscription_2019', 'inscription', 'hello@mail.fr', $langcode, $params, $reply, $send);
```

