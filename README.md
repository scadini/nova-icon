## Nova Icon 
[![Latest Stable Version](https://poser.pugx.org/scadini/nova-icon/v/stable)](https://packagist.org/packages/scadini/nova-icon)
[![License](https://poser.pugx.org/scadini/nova-icon/license)](https://packagist.org/packages/scadini/nova-icon)

This package allows you to render a SVG icon as a custom field.

[Available Icons](#available-icons) | [Examples](#example) | [Roadmap](#roadmap)
___
### Installation
```bash
composer require scadini/nova-icon
```

### Usage
```php
use NovaIcon\Icon;
```

```php
public function fields()
{
    return [
        ID::make()->sortable(),

        Text::make('Name'),

        Icon::make('Approved')
            ->icon('entypo:check'),
    ];
}
```
<img src="https://github.com/scadini/nova-icon/blob/master/img/example_1.png" alt="Example 1">

___
The simplest way to add an icon is by using the `icon()` method. 
This method accepts either a string or a closure containing the **vendor name** and the **icon name** separated by a **colon**:

````php
    Icon::make('Approved')->icon('entypo:check');
````

````php
    Icon::make('Approved')->icon(function () {
        return 'entypo:check';
    });
````

To apply css classes, you can chain the `css()` method. This method accepts a string, an array, or a closure:

````php
    Icon::make('Approved')->icon('entypo:check')->css('text-info h-12 w-12');

    Icon::make('Approved')->icon('entypo:check')->css(['text-info', 'h-12', 'w-12']);

    Icon::make('Approved')
        ->icon('entypo:check')
        ->css(function () {
            return 'text-info h-12 w-12'; // or ['text-info', 'h-12', 'w-12']
        }
    );
````

To hide an icon for a specific row, you can use the `hide()` method. This method accepts a closure:

````php
    Icon::make('Approved')
        ->icon('entypo:check')
        ->hide(function () {
            return $this->role === 'admin';
        });
````

### Example

Here's an example about using this component. Let's say a user has a preferred internet platform:

```php
    Icon::make('Platform')
        ->icon(function () {
            return 'entypo:' . $this->platform;
        })
        ->css(function () {
            $options = [
                'youtube' => 'text-danger',
                'vimeo'   => 'text-success'
            ];

            return $options[$this->platform];
        })
```

<img src="https://github.com/scadini/nova-icon/blob/master/img/example_2.png" alt="Example 2">

---
## Available Icons

The icons available are organized by their vendor name.

Currently, the only vendor available is [Entypo](http://www.entypo.com/), 
but there are plans to include [Zondicons](https://www.zondicons.com/icons.html) library.

For the icon names you can use [this reference table](https://github.com/hypermodules/entypo#icon-names)
___

## Roadmap
- [ ] Add all icons from Entypo
- [ ] Add all icons from Zondicons
- [ ] Make icons clickable to perform actions or view resources
