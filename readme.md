## Duplicate hidden fields

Drupal Module for duplicate fields using [Drupal's Form API](http://api.drupal.org/api/drupal/developer%21topics%21forms_api_reference.html/7).

Some forms might have to look like this:
```html
  <form action="submit.php" method="get">
    <input type="hidden" name="key" value="value1">
    <input type="hidden" name="key" value="value2">
    <input type="submit">
  </form>
```
In your typical `$_GET["key"]` or `$_POST["key"]` the value will be value2, but value1 is accessible via `$_SERVER['QUERY_STRING']` (for `$_GET`) or `file_get_contents('php://input')` (for `$_POST`).

### Usage

It is not recommended to use this element for common form tasks. It can come in handy when talking to API's that require these types of fields via POST.

Add the following code to a $form array:

```php
$form['testhidden'] = array(
  '#type' => 'duplicate_hidden_field',
  '#value' => array("one","two"),
);
```