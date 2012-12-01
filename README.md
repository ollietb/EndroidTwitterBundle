Endroid Twitter Bundle
======================

[![Build Status](https://secure.travis-ci.org/endroid/EndroidTwitterBundle.png)](http://travis-ci.org/endroid/EndroidTwitterBundle)

This bundle enables you to use the Endroid Twitter (endroid/Twitter) library as a decoupled service and enables configuration
through the Symfony framework. Endroid Twitter is a service that helps developers to make calls to Twitter, without bothering
about generating request headers, oauth and such. For more information see the [endroid/Twitter](https://github.com/endroid/Twitter)
repository and the [Twitter API](https://dev.twitter.com/docs/api/1.1).

[![knpbundles.com](http://knpbundles.com/endroid/EndroidTwitterBundle/badge-short)](http://knpbundles.com/endroid/EndroidTwitterBundle)

## Requirements

* Symfony
* Dependencies:
 * [`Buzz`](https://github.com/kriswallsmith/Buzz)
 * [`Twitter`](https://github.com/endroid/Twitter)

## Installation

### Add in your composer.json

```js
{
    "require": {
        "endroid/twitter-bundle": "dev-master"
    }
}
```

### Install the bundle

``` bash
$ curl -s http://getcomposer.org/installer | php
$ php composer.phar update endroid/twitter-bundle
```

Composer will install the bundle to your project's `vendor/endroid` directory.

### Enable the bundle via the kernel

``` php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Endroid\Bundle\TwitterBundle\EndroidTwitterBundle(),
    );
}
```

## Configuration

### config.yml

```yaml
endroid_twitter:
    consumer_key: "..."
    consumer_secret: "..."
    access_token: "..."
    access_token_secret: "..."
```

## Usage

After installation and configuration, the service can be directly referenced from within your controllers.

```php
<?php
public function getTimelineAction()
{
    $twitter = $this->get('endroid.twitter');
    $timeline = $twitter->getTimeline();

    ...
}
```