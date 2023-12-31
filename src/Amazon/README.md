# Amazon

```bash
composer require socialiteproviders/amazon
```

## Installation & Basic Usage

Please see the [Base Installation Guide](https://socialiteproviders.com/usage/), then follow the provider specific instructions below.

### Add configuration to `config/services.php`

```php
'amazon' => [
    'client_id' => env('AMAZON_SIGNIN_CLIENT_ID'),
    'client_secret' => env('AMAZON_SIGNIN_SECRET'),
    'redirect' => env('AMAZON_SIGNIN_REDIRECT_URI')
],
```

### Add provider event listener

Configure the package's listener to listen for `SocialiteWasCalled` events.

Add the event to your `listen[]` array in `app/Providers/EventServiceProvider`. See the [Base Installation Guide](https://socialiteproviders.com/usage/) for detailed instructions.

```php
protected $listen = [
    \SocialiteProviders\Manager\SocialiteWasCalled::class => [
        // ... other providers
        \SocialiteProviders\Amazon\AmazonExtendSocialite::class.'@handle',
    ],
];
```

### Usage

You should now be able to use the provider like you would regularly use Socialite (assuming you have the facade installed):

```php
return Socialite::driver('amazon')->redirect();
```

### Returned User fields

- ``id``
- ``nickname``
- ``name`` (same as ``nickname``)
- ``email``
