# OneSignal Web Push SDK (mrf version)

branch from the **marfeel** branch, and merge into it.

this branch will be rebased with OneSignal's OneSignal-Website-SDK master

generate bundle
```sh
# generate the bundle
npm run build:prod

# move it to XP
cp ./build/bundles/OneSignalSDK.js $MARFEELXP_HOME/Tenants/vhosts/marfeel/resources/pushNotifications/OneSignalSDK.js
```

## debug

You should be able to run commands in the developer tools Console now.

Execute the following code in console:

```js
OneSignal.log.setLevel('trace');
```
You should see undefined as the result. Reloading the page will provide you all the debug call of OneSignal.

If you see:

Uncaught ReferenceError: OneSignal is not defined(…) or ReferenceError: OneSignal is not defined, then OneSignal is not active on your webpage.

Reference: [Web Push Troubleshooting](https://documentation.onesignal.com/docs/troubleshooting-web-push)

## checks
in chrome dev tools (remember that Push notifications do not work in incognito)

```js
OneSignal.VERSION
// it should return 150300 (defined in package.json)
```

accept push notifications and send a push notification
```js
OneSignal.sendSelfNotification(
 /* Title (defaults if unset) */ "Title",
 /* Message (defaults if unset) */ "Text",
  /* URL (defaults if unset) */ 'https://example.com/?_osp=do_not_open',
 /* Icon */ 'https://onesignal.com/images/notification_logo.png'
);
```

## mrf changelog
* update package.json and return always the sdk version specified in the package.json config [PR](https://github.com/Marfeel/OneSignal-Website-SDK/pull/1)
* get AppId from indexedDB instead of the qureyparams [PR](https://github.com/Marfeel/OneSignal-Website-SDK/pull/3)
* integrate OneSignal Typical site integration with marfeel service workers [PR](https://github.com/Marfeel/OneSignal-Website-SDK/pull/9)
