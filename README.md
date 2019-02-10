# Heroku App Pinger
JavaScript ping tool to keep personal free Heroku app dynos from sleeping every 30 minutes. For use in a web browser context. Built on the pingjs API, created by Jonathan Frederic. Released under the BSD-3-Clause license, see
LICENSE.

## Usage
Download or clone the repository and open `ping.html`. Input the desired Heroku app name and number of hours you'd like the pinger to run, and click `Ping`. Open the browser's JavaScript console to view the ping log.

Since this code is run from the client, the browser window must be left open and your computer running for the duration of the desired ping loop.

The pingjs library uses a  [UMD header](https://github.com/umdjs/umd/blob/master/templates/returnExports.js)
that allows it to be loaded as CommonJS, AMD, or a window global object.  

A single function is exported, `ping`.  Ping's signature follows:  

```js
/**
 * Pings a url.
 * @param  {String} url
 * @param  {Number} multiplier - optional, factor to adjust the ping by.  0.3 works well for HTTP servers.
 * @return {Promise} promise that resolves to a ping (ms, float).
 */
```

Example:  

```js
ping('https://google.com/').then(function(delta) {
    console.log('Ping time was ' + String(delta) + ' ms');
}).catch(function(err) {
    console.error('Could not ping remote URL', err);
});
```

## Caveats

The user should be aware that this method relies on the HTTP protocol to ping
remote URLs.  Consequently, ping times are not as reliable as if they were
performed using the ICMP protocol.  
