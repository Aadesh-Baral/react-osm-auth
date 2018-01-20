# react-osm-auth [![Build Status](https://travis-ci.org/drklrd/react-osm-auth.svg?branch=master)](https://travis-ci.org/drklrd/react-osm-auth)

A React component for authentication with [OpenStreetMap](http://www.openstreetmap.org/). This is based on [osm-auth](https://github.com/osmlab/osm-auth) created by osmlab.

### Installation 

```sh
npm install react-osm-auth --save
```

### Usage

```js
import  ReactOSMAuth from 'react-osm-auth';

const options = {
    url : 'https://master.apis.dev.openstreetmap.org',
    oauth_consumer_key: 'your consumer key',
    oauth_secret: 'your secret key',
    auto: true,
};


class Test extends React.Component {
    
  onAuthenticated(details){
          console.log('details',details) // an XML DOM of user details
  }
  
  render() {
          return (
              <div>
                  <ReactOSMAuth {...options} onAuthenticated={this.onAuthenticated.bind(this)}/>
              </div>
          );
      }
}
```

This component also exposes 'onAuthenticated' method to handle user details on authentication.

### Required Landing page

For this component to work(as with osm-auth by osmlab) , you need to add a HTML landing page for the Auth Popup. The default name for the popup is 'land.html' and is also included in this repo.
Add that html file in the same directory where your 'index.html' for the app resides. The "land.html" page should have the following content.

```html
<!DOCTYPE html>
<html><head></head>
    <body>
        <script>
            opener.authComplete(window.location.href);
            window.close();
        </script>
    </body>
</html>
```
