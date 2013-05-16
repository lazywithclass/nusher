# A pusher client for the node.js

This is a (diverged) fork of Abhishiv's work at https://github.com/abhishiv/pusher-node-client, so credit to him for writing this in the first place.

## How to use

```javascript
PusherClient = require('nusher')

pusher_client = new PusherClient
  appId: (process.env.PUSHER_APP_ID or app_id)
  key: (process.env.PUSHER_KEY or pusher_key)
  secret: (process.env.PUSHER_SECRET or pusher_secret)

pusher_client.on 'connect', ->
  channel = pusher_client.subscribe('presence-users', {user_id: 'system'})

  channel.on 'success', () ->

    channel.on 'pusher_internal:member_removed', (data) ->
      console.log 'member_removed'

    channel.on 'pusher_internal:member_added', (data) ->
      console.log 'member_added'

pusher_client.connect()
```

## License

This code is free to use under the terms of the MIT license.
