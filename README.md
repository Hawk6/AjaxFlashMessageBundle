# AjaxFlashMessageBundle
Symfony bundle to handle symfony flash messages called by ajax actions

Bundle will catch all FlashBag messages set in ajax actions in controllers when send an request via jquery and display it as it would show flash messages used in normal symfony controller actions.
You can override flash message styles as you wish. At the moment they should look quite user friendly/UX.

# Installation

Add AretusaFlashBundle in your composer.json file:
```json
{
    "require": {
        "aretusa/flash-bundle": "~1.0"
    }
}
```
Now tell Composer to download the bundle by running the command:
```console
php composer.phar update aretusa/flash-bundle
```
Composer will install the bundle to your project's vendor/aretusa directory.

# Step 2: Enable the bundle

Enable the bundle in the kernel:

```php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Aretusa\Bundle\FlashBundle\AretusaFlashBundle(),
    );
}
```
# Step 3: Publish assets
```console
php app/console assets:install web --symlink --relative
```
# Step 4: Include the messages template

In layout file:
```twig
{{ include('AretusaFlashBundle::flash-messages.html.twig') }}
```
# Step 5: add assets to your main layout file

Add jQuery as well if it's not already done.
```twig
{% block javascripts %}
    // ...
    <script src="//code.jquery.com/jquery-2.1.3.min.js" type="text/javascript"></script>
    <script src="{{ asset('bundles/aretusaflash/js/flash-message.js') }}" type="text/javascript"></script>
{% endblock %}
{% block stylesheets %}
    // ...
    <link href="{{ asset('bundles/aretusaflash/css/flash-message.css') }}" type="text/css" rel="stylesheet" />
{% endblock %}
```
# Usage

Add this call to a script block in your layout or to some of your templates:
```html
<script>
$('#flash-messages').flashNotification('init');
</script>
```
