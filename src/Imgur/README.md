# Imgur

```bash
composer require socialiteproviders/imgur
```

## Installation & Basic Usage

Please see the [Base Installation Guide](https://socialiteproviders.com/usage/), then follow the provider specific instructions below.

### Add configuration to `config/services.php`

```php
'imgur' => [    
  'client_id' => env('IMGUR_CLIENT_ID'),  
  'client_secret' => env('IMGUR_CLIENT_SECRET'),  
  'redirect' => env('IMGUR_REDIRECT_URI') 
],
```

### Add provider event listener

Configure the package's listener to listen for `SocialiteWasCalled` events.

Add the event to your `listen[]` array in `app/Providers/EventServiceProvider`. See the [Base Installation Guide](https://socialiteproviders.com/usage/) for detailed instructions.

```php
protected $listen = [
    \SocialiteProviders\Manager\SocialiteWasCalled::class => [
        // ... other providers
        \SocialiteProviders\Imgur\ImgurExtendSocialite::class.'@handle',
    ],
];
```

### Usage

You should now be able to use the provider like you would regularly use Socialite (assuming you have the facade installed):

```php
return Socialite::driver('imgur')->redirect();
```

### Returned User fields

- ``id``
- ``nickname``
- ``name`` (same as ``nickname``)
- ``email``
