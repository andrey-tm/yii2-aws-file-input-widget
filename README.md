# yii2-aws-file-input-widget
Yii2 widget allows to integrate AWS S3 file upload. Based on [File Input](https://github.com/kartik-v/bootstrap-fileinput).

## Installation

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require andreyv/yii2-aws-file-input-widget "^1.0"
```

or add

```
"andreyv/yii2-aws-file-input-widget": "^1.0"
```

to the require section of your `composer.json` file.

## Usage

Add the following to your config file

```php
'components' => [
        ...
        'aws' => [
            'class' => 'andreyv\aws\fileinput\components\Aws',
            'credentials' => [
                'key' => 'aws-access-key',
                'secret' => 'aws-secret,
            ],
            'region' => 'aws-region',
            'bucket' => 'bucket-name',
        ],
        ...
    ],

```

Use with ActiveForm

```php
echo $form->field($model, 'image')->widget(AwsFileInput::class, [
    'options' => ['accept' => 'image/*'], //acceptable files
]);
```

```php
echo $form->field($model, 'image')->widget(AwsFileInput::class, [
    'awsComponent' => 'awsComponentName', //custom component name, `aws` by default
    'uniqueKey' => 'uniqueKey', //model unique attribute, `id` by default
    'options' => ['accept' => 'image/*'], //acceptable files
]);
```

```php
echo $form->field($model, 'image')->widget(AwsFileInput::class, [
    'awsComponent' => 'awsComponentName', //custom component name, `aws` by default
    'fileNameParts' => 'uniqueKey', //custom file name parts, if not set `uniqueKey` will be used
    'options' => ['accept' => 'image/*'], //acceptable files
]);
```

