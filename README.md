# Send mail
Plugin for send mail to admin use SMTP

## Install
Clone from git
```bash
cd </path_to_project>/wp-content/plugins
git clone https://github.com/AkinaySau/wp-plugin-send-mail.git send-mail

cd send-mail
composer install
```
or as composer project
```bash
cd </path_to_project>/wp-content/plugins
composer create-project sau/wp-plugin-send-mail send-mail
``` 

## WP Filters

**sau_send_mail__subject_messages** - for change of a subject of the message
```php
add_filter('sau_send_mail__body_messages', function ($subject) {
        //your code
        return $subject
    }
);

```

**sau_send_mail__body_messages** - To create an e-mail message for the template you want
```php
add_filter('sau_send_mail__body_messages', function ($val, $vars) {
        $output = '<table><tbody>';
        $data   = json_decode($vars[ 'formData' ]);

        foreach ($data as $item) {
            $output .= sprintf('<tr><tb><b>%s</b></tb><td>%s</td></tr>', $item->title, $item->value);
        }
        $output .= '</tbody></table>';

        return $output;
    }, 10, 2
);

`
