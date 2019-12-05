# Rdx

Redux, but smaller ...

This is a simple immutable state store along the lines of Redux but significantly 
smaller. It helps to build apps with super-small JavaScript payloads. It provides 
all the basic features for creating a client-side app including:

Redux-like state store (actions / reducers / middleware)
Root reducer utility function (combineReducers)
Handling of async actions (aka 'thunks')
Mixin to connect custom elements to the store (map state to properties and events to store dispatch)

Total size: 1.45 Kb minified / 615 bytes gzipped

With additional enhancements:

Redux DevTools integration for debug and time-travel
State hydration & persistence using localStorage

Total size: 2.11 Kb minified / 921 bytes gzipped

## Compatibility

The store takes advantage of existing web platform features instead of
adding JS code to replicate them. The ability to subscribe to the store
for state changes and to handle dispatched actions (middleware) relies on
[`EventTarget`](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget).
Unfortunately, the `EventTarget` _constructor()_ is not currently supported
on WebKit so if you want to support Safari users, an extra small (589 byte)
polyfill is needed:

```html
<script src="https://unpkg.com/@ungap/event-target@0.1.0/min.js"></script>
```

Once [support is added](https://bugs.webkit.org/show_bug.cgi?id=174313)
this polyfill can be removed.

## Plans

To avoid the normal bloat of boiler-plate code that Redux can introduce
I'm also working on a way to define the state, reducers and effects all
in a single object similar to `redux-rematch` to make working with the
store easier and also allow your app code to be kept to a minimum.

This will also include a store-integrated router module based on a tiny
routing system.

Together, this will make it possible to have a fully functioning app
complete with routing, async data fetching, persistence and UI components
in approximately 8 Kb of minified JS, around 3.0 Kb compressed.
