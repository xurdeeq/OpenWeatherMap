Endroid OpenWeatherMap
======================

*By [endroid](http://endroid.nl/)*

[![Latest Stable Version](http://img.shields.io/packagist/v/endroid/openweathermap.svg)](https://packagist.org/packages/endroid/openweathermap)
[![Build Status](https://secure.travis-ci.org/endroid/OpenWeatherMap.png)](http://travis-ci.org/endroid/OpenWeatherMap)
[![Total Downloads](http://img.shields.io/packagist/dt/endroid/openweathermap.svg)](https://packagist.org/packages/endroid/openweathermap)
[![Monthly Downloads](http://img.shields.io/packagist/dm/endroid/openweathermap.svg)](https://packagist.org/packages/endroid/openweathermap)
[![License](http://img.shields.io/packagist/l/endroid/openweathermap.svg)](https://packagist.org/packages/endroid/openweathermap)

OpenWeatherMap helps making requests to the OpenWeatherMap API, without having to bother too much about passing your API
key and building requests. The only thing you need is the API key (APPID) which you can find after [registration on the
website](http://openweathermap.org/login).

More info about custom parameters in the official API docs: http://bugs.openweathermap.org/projects/api/wiki/Api_2_5

```php
use Endroid\OpenWeatherMap\Client;

$apiKey = '...';
$client = new Client($apiKey);

// Retrieve the current weather for Breda
$weather = $client->getWeather('Breda,nl');

// Or retrieve the weather using the generic query method
$response = $client->query('weather', ['q' => 'Breda,nl']);
$weather = json_decode($response->getContent());

// You can also retrieve a N days forecast
$forecast = $client->getForecast('Breda,nl', 7);

```

## Symfony integration

Register the Symfony bundle in the kernel.

```php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = [
        // ...
        new Endroid\OpenWeatherMap\Bundle\EndroidOpenWeatherMapBundle(),
    ];
}

```

The default parameters can be overridden via the configuration.

```yaml
endroid_open_weather_map:
    api_key: '...'
    units: 'metric'

```

Now you can retrieve the client as follows.

```php
$client = $this->get('endroid.open_weather_map.client');

```

## Versioning

Version numbers follow the MAJOR.MINOR.PATCH scheme. Backwards compatibility
breaking changes will be kept to a minimum but be aware that these can occur.
Lock your dependencies for production and test your code when upgrading.

## License

This bundle is under the MIT license. For the full copyright and license
information please view the LICENSE file that was distributed with this source code.
