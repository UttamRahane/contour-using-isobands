<template>
  <div class="map-container">
    <div id="mapbox-map"/>
    <canvas id="deck-canvas"/>
  </div>
</template>

<script>
import mapboxgl from "mapbox-gl";
import { Deck } from "@deck.gl/core";
//import { SolidPolygonLayer } from "@deck.gl/layers";
import isobands from "@turf/isobands";
import pointGrid from "@turf/point-grid";
import bbox from "@turf/bbox";
import circle from "@turf/circle";
import pointsWithinPolygon from "@turf/points-within-polygon";
export default {
  name: "MapComponent",
  data: () => {
    return {
      deck: null,
      map: null
    };
  },
  mounted() {
    if (!mapboxgl.supported()) {
      alert("your browser is unsupported");
    } else {
      this.initMap();
    }
  },
  methods: {
    initMap() {
      mapboxgl.accessToken =
        "pk.eyJ1IjoibGFicy1zYW5kYm94IiwiYSI6ImNrMTZuanRtdTE3cW4zZG56bHR6MnBkZG4ifQ.YGRP0sZNYdLw5_jSa9IvXg";
      this.map = new mapboxgl.Map({
        container: "mapbox-map",
        interactive: false,
        style: `mapbox://styles/mapbox/streets-v11`,
        center: [0, 0],
        zoom: 3,
        pitch: 0
      });
      this.map.on("style.load", () => {
        this.initDeck();
      });
    },
    initDeck() {
      this.deck = new Deck({
        canvas: "deck-canvas",
        width: "100%",
        height: "100%",
        initialViewState: {
          latitude: 0,
          longitude: 0,
          zoom: 3,
          center: [0, 0],
          pitch: 0
        },
        controller: true,
        onViewStateChange: ({ viewState, interactionState }) => {
          this.map.jumpTo({
            center: [viewState.longitude, viewState.latitude],
            zoom: viewState.zoom,
            pitch: viewState.pitch,
            bearing: viewState.bearing
          });
        }
      });
      this.addLayer();
    },
    addLayer() {
      let data = {
        type: "FeatureCollection",
        features: [
          {
            type: "Feature",
            properties: {
              value: 17.11178505181615
            },
            geometry: {
              type: "Point",
              coordinates: [-97.43621, 40.18826]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 8.872193054360507
            },
            geometry: {
              type: "Point",
              coordinates: [-101.21119, 32.07437]
            }
          },
          {
            type: "Feature",
            properties: {
              value: -1000.26931731610456
            },
            geometry: {
              type: "Point",
              coordinates: [-97.1945, 34.55289]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 4.738838704901372
            },
            geometry: {
              type: "Point",
              coordinates: [-105.21453, 34.75171]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 7.807800856288778
            },
            geometry: {
              type: "Point",
              coordinates: [-101.81544, 33.75283]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 18.76641471820555
            },
            geometry: {
              type: "Point",
              coordinates: [-101.9253, 32.66822]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 19.638936584188905
            },
            geometry: {
              type: "Point",
              coordinates: [-97.43621, 40.18826]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 4.915447627359989
            },
            geometry: {
              type: "Point",
              coordinates: [-98.77654, 40.12109]
            }
          },
          {
            type: "Feature",
            properties: {
              value: -3.552713678800501e-15
            },
            geometry: {
              type: "Point",
              coordinates: [-103.08318, 40.10428]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 20.70961444648663
            },
            geometry: {
              type: "Point",
              coordinates: [-106.09344, 40.22183]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 14.36450347932001
            },
            geometry: {
              type: "Point",
              coordinates: [-106.75262, 40.35591]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 22.01925874228332
            },
            geometry: {
              type: "Point",
              coordinates: [-109.05975, 36.20101]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.753232930641076
            },
            geometry: {
              type: "Point",
              coordinates: [-107.23602, 39.13959]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 22.477078860919185
            },
            geometry: {
              type: "Point",
              coordinates: [-104.42352, 39.20773]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 22.951547769554015
            },
            geometry: {
              type: "Point",
              coordinates: [-105.14861, 38.29958]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.828292801687898
            },
            geometry: {
              type: "Point",
              coordinates: [-102.75359, 36.97727]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 28.036430263287976
            },
            geometry: {
              type: "Point",
              coordinates: [-100.99578, 32.96368]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 24.93236167338472
            },
            geometry: {
              type: "Point",
              coordinates: [-102.62176, 32.87146]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 24.93236167338472
            },
            geometry: {
              type: "Point",
              coordinates: [-102.84148, 31.34537]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 20.953766915603076
            },
            geometry: {
              type: "Point",
              coordinates: [-102.53387, 31.11991]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 19.577976194557223
            },
            geometry: {
              type: "Point",
              coordinates: [-96.46941, 30.7996]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 23.608430767858366
            },
            geometry: {
              type: "Point",
              coordinates: [-97.1725, 31.34537]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 0
            },
            geometry: {
              type: "Point",
              coordinates: [-97.19451, 34.55289]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 18.0459531256743
            },
            geometry: {
              type: "Point",
              coordinates: [-105.21453, 34.75171]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 17.404374567839525
            },
            geometry: {
              type: "Point",
              coordinates: [-101.85271, 33.60656]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 23.445436113683634
            },
            geometry: {
              type: "Point",
              coordinates: [-108.51814, 53.07403]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 18.33103635735441
            },
            geometry: {
              type: "Point",
              coordinates: [-111.72469, 51.56852]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 26.606680692018777
            },
            geometry: {
              type: "Point",
              coordinates: [-106.77875, 53.61042]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 27.554422125540043
            },
            geometry: {
              type: "Point",
              coordinates: [-108.84773, 53.10043]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 19.35905369149223
            },
            geometry: {
              type: "Point",
              coordinates: [-111.72469, 51.56852]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.77346474088894
            },
            geometry: {
              type: "Point",
              coordinates: [-110.05477, 55.8059]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 29.330306486645224
            },
            geometry: {
              type: "Point",
              coordinates: [-109.46151, 55.49596]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 25.14325761160459
            },
            geometry: {
              type: "Point",
              coordinates: [-111.10946, 54.58956]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 23.657662089999995
            },
            geometry: {
              type: "Point",
              coordinates: [-111.35116, 54.42371]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 24.549026833225458
            },
            geometry: {
              type: "Point",
              coordinates: [-110.07674, 53.81848]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 22.283716637004183
            },
            geometry: {
              type: "Point",
              coordinates: [-110.93368, 53.05936]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 19.91745016696619
            },
            geometry: {
              type: "Point",
              coordinates: [-108.38485, 53.83145]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 19.891201433976857
            },
            geometry: {
              type: "Point",
              coordinates: [-110.58211, 52.33729]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.304647141061565
            },
            geometry: {
              type: "Point",
              coordinates: [-106.1766, 52.63833]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.031745506124484
            },
            geometry: {
              type: "Point",
              coordinates: [-105.75912, 52.95718]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.17935633986279
            },
            geometry: {
              type: "Point",
              coordinates: [-105.40755, 52.16915]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.105550944598967
            },
            geometry: {
              type: "Point",
              coordinates: [-106.30843, 51.8988]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.105550944598967
            },
            geometry: {
              type: "Point",
              coordinates: [-106.65999, 52.15567]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.093501222208683
            },
            geometry: {
              type: "Point",
              coordinates: [-105.49544, 52.46465]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.172588201219728
            },
            geometry: {
              type: "Point",
              coordinates: [-107.64876, 52.55826]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.228214949131253
            },
            geometry: {
              type: "Point",
              coordinates: [-108.28597, 50.50847]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.95907320269035
            },
            geometry: {
              type: "Point",
              coordinates: [-109.25277, 50.17191]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.28787929468982
            },
            geometry: {
              type: "Point",
              coordinates: [-106.77875, 53.61042]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 21.3086294902139
            },
            geometry: {
              type: "Point",
              coordinates: [-108.6684, 52.98006]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 13.343983942916697
            },
            geometry: {
              type: "Point",
              coordinates: [-86.5651, 49.67393]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 19.983547469999998
            },
            geometry: {
              type: "Point",
              coordinates: [-90.73991, 54.67946]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 0
            },
            geometry: {
              type: "Point",
              coordinates: [-91.83854, 52.56892]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 4.138383277594974
            },
            geometry: {
              type: "Point",
              coordinates: [-95.13444, 52.88827]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 22.25824691190355
            },
            geometry: {
              type: "Point",
              coordinates: [-86.5651, 49.67393]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 25.83285102930552
            },
            geometry: {
              type: "Point",
              coordinates: [-91.09147, 49.95749]
            }
          },
          {
            type: "Feature",
            properties: {
              value: -0.9309110821784766
            },
            geometry: {
              type: "Point",
              coordinates: [-91.39909, 50.23938]
            }
          },
          {
            type: "Feature",
            properties: {
              value: -6.84929232896242
            },
            geometry: {
              type: "Point",
              coordinates: [-91.75065, 50.32363]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 16.61409393673287
            },
            geometry: {
              type: "Point",
              coordinates: [-91.39909, 51.21299]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 11.611491726078288
            },
            geometry: {
              type: "Point",
              coordinates: [-92.76139, 51.10274]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 18.160285128548676
            },
            geometry: {
              type: "Point",
              coordinates: [-94.21159, 50.96456]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 20.70961444648663
            },
            geometry: {
              type: "Point",
              coordinates: [-96.18913, 51.07514]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 19.727872808055327
            },
            geometry: {
              type: "Point",
              coordinates: [-96.98014, 51.1579]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 18.936457877712662
            },
            geometry: {
              type: "Point",
              coordinates: [-97.19987, 52.9942]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 19.169982167141647
            },
            geometry: {
              type: "Point",
              coordinates: [-93.72819, 51.92318]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 19.186514617871264
            },
            geometry: {
              type: "Point",
              coordinates: [-90.25651, 54.75561]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 20.02352056310915
            },
            geometry: {
              type: "Point",
              coordinates: [-91.83854, 52.56892]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 20.44424546681932
            },
            geometry: {
              type: "Point",
              coordinates: [-93.42057, 53.62436]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 19.34700917417186
            },
            geometry: {
              type: "Point",
              coordinates: [-90.73991, 54.67946]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 19.199166693003594
            },
            geometry: {
              type: "Point",
              coordinates: [-93.28874, 53.85827]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 18.669904576337807
            },
            geometry: {
              type: "Point",
              coordinates: [-93.59635, 54.65405]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 16.14262537303571
            },
            geometry: {
              type: "Point",
              coordinates: [-95.13444, 52.88827]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 18.463588641990974
            },
            geometry: {
              type: "Point",
              coordinates: [-99.44108, 54.03931]
            }
          },
          {
            type: "Feature",
            properties: {
              value: 18.39183397841253
            },
            geometry: {
              type: "Point",
              coordinates: [-101.41862, 54.01349]
            }
          }
        ]
      };
      // create grid where data is available
      let points = pointGrid(bbox(data), 80, {
        units: "miles"
      });
      for (let d of data.features) {
        const nearestArea = circle(d.geometry.coordinates, 100, {
          steps: 10,
          units: "miles"
        });
        const pointsInRedius = pointsWithinPolygon(points, nearestArea);
        for (let p of pointsInRedius.features) {
          if (p.properties.value) {
            p.properties.value += d.properties.value;
          } else {
            p.properties.value =
              d.properties.value !== 0 ? d.properties.value : 0.0001;
          }
        }
      }
      for (let i of points.features) {
        if (i.properties.value === undefined) {
          i.properties.value = 0;
        }
      }
      let maxValue = Math.max(...points.features.map(x => x.properties.value));
      let breaks = [
        -Infinity,
        0.0001,
        maxValue / 10,
        (maxValue / 10) * 2,
        (maxValue / 10) * 3,
        (maxValue / 10) * 4,
        (maxValue / 10) * 5,
        (maxValue / 10) * 6,
        (maxValue / 10) * 7,
        (maxValue / 10) * 8,
        (maxValue / 10) * 9,
        maxValue
      ];
      let bands = isobands(points, breaks, { zProperty: "value" });
      //console.log(bands);
      this.map.addSource("bands", {
        type: "geojson",
        data: bands
      });
      this.map.addLayer({
        id: "maine",
        type: "fill",
        source: "bands",
        paint: {
          "fill-color": [
            "match",
            ["get", "value"],
            "-Infinity-0.0001",
            "#66c2a5",
            "0.0001-" + maxValue / 10,
            "#ffffcc",
            maxValue / 10 + "-" + (maxValue / 10) * 2,
            "#ffeda0",
            (maxValue / 10) * 2 + "-" + (maxValue / 10) * 3,
            "#fed976",
            (maxValue / 10) * 3 + "-" + (maxValue / 10) * 4,
            "#feb24c",
            (maxValue / 10) * 4 + "-" + (maxValue / 10) * 5,
            "#fd8d3c",
            (maxValue / 10) * 5 + "-" + (maxValue / 10) * 6,
            "#fc4e2a",
            (maxValue / 10) * 6 + "-" + (maxValue / 10) * 7,
            "#e31a1c",
            (maxValue / 10) * 7 + "-" + (maxValue / 10) * 8,
            "#bd0026",
            (maxValue / 10) * 8 + "-" + (maxValue / 10) * 9,
            "#800026",
            (maxValue / 10) * 9 + "-" + maxValue,
            "#FF0000",
            "#FF0000"
          ],
          "fill-opacity": 0.7
        }
      });
      // const FILL_LAYER = new SolidPolygonLayer({
      //   id: "fill",
      //   data: bands.features,
      //   getPolygon: d => {
      //     console.log(d.geometry);
      //     return d.geometry.coordinates;
      //   },
      //   getFillColor: [255, 255, 178],
      //   extruded: false,
      //   opacity: 0.25
      // });
      // this.deck.setProps({ layers: [FILL_LAYER] });
    }
  }
};
</script>
<style scoped>
.map-container {
  position: relative;
  height: 100vh;
  width: 100vw;
}
#mapbox-map {
  width: 100%;
  height: 100%;
  position: absolute;
}
</style>
