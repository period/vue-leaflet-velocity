# vue-leaflet-velocity
So, there's this: https://github.com/danwild/leaflet-velocity
And there's this: https://github.com/vue-leaflet/Vue2Leaflet
...and apparently they take a lot of effort to get to work together.

TBH, I have no idea how many bad practices were used to get this to work. I spent several hours examining how other plugins worked and came up with this and it seems to work fine.

To use:

```
<l-velocity-layer v-if="wind_options != null" :options="wind_options" />
```
