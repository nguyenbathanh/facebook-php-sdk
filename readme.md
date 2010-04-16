Facebook Connect PHP SDK
========================

Facebook [Connect][Connect] is a set of APIs that make your application more
social. With it you gain access to:

1. Identity: the user's name, photo and more [User][FQL_User].
2. The Graph: the user's friends and connections
   [Connection][FQL_Connection].
3. Distribution: the Stream, and the ability to communicate
   [Publishing][Publishing].
4. Integration: publishers, canvas pages, profile tabs.


[Connect]: http://developers.facebook.com/connect "Facebook | Connect"
[FQL_User]: http://wiki.developers.facebook.com/index.php/User_(FQL) "FQL User Table"
[FQL_Connection]: http://wiki.developers.facebook.com/index.php/Connection_(FQL) "FQL Connection Table"
[Publishing]: http://wiki.developers.facebook.com/index.php/Stream.publish "Stream Publishing"

This repository contains the open source PHP SDK that allows you to utilize the
above on your website. Except as otherwise noted, the Facebook Connect PHP SDK
is licensed under the Apache Licence, Version 2.0
(http://www.apache.org/licenses/LICENSE-2.0.html)


Status
------

This is an **alpha** release. In order to guide the development of the library
and allow you to freely inspect and use the source, we have open sourced the
client PHP SDK. We do not have all the features we intend to build, but we will
be building them incrementally in a transparent manner.

Currently, we have the first iteration of the PHP APIs that allow you to:

- Handle Authentication
- Make API calls


Usage
-----

The [examples][examples] are a good place to start. The minimal you'll need to
have is:

    <?php

    require './facebook.php';

    $facebook = new Facebook(array(
      'appId'  => 'YOUR APP ID',
      'secret' => 'YOUR API SECRET',
      'cookie' => true, // enable optional cookie support
    ));

To make [API][API] calls:

    try {
      $me = $facebook->api('/me');
    } catch (FacebookApiException $e) {
      error_log($e);
    }

Logged in vs Logged out:

    if ($facebook->getSession()) {
      echo '<a href="' . $facebook->getLogoutUrl() . '">Logout</a>';
    } else {
      echo '<a href="' . $facebook->getLoginUrl() . '">Login</a>';
    }

[examples]: php-sdk/tree/master/index.php
[API]: http://wiki.developers.facebook.com/index.php/API


Feedback
--------

We are relying on the [GitHub issues tracker][issues] linked from above for
feedback. File bugs or other issues [here][issues].

[issues]: http://github.com/facebook/php-sdk/issues



Tests
-----

We are working hard to ensure your experience using Connect is stable. In order
to keep us nimble and allow us to bring you new functionality, without
compromising on stability, we have ensured full test coverage of the new SDK.
We are including this in the open source repository to assure you of our
commitment to quality, but also with the hopes that you will contribute back to
help keep it stable. The easiest way to do so is to file bugs and include a
test case.
