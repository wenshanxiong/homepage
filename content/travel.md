---
title: "Travel"
date: 2024-01-01
draft: false
---

# Where I've Been

Explore the places I've been to around the world. Click on the pins to learn more about each destination.

<div id="travel-map" style="height: 400px; width: 100%; max-width: 600px; margin: 20px auto; border-radius: 8px; box-shadow: 0 2px 10px rgba(0,0,0,0.1);"></div>

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<script>
// Initialize the map with continuous scrolling
var map = L.map('travel-map', {
    worldCopyJump: true,
    minZoom: 1
}).setView([0, 180], 1);

// Add tile layer with world wrapping enabled
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '© OpenStreetMap contributors',
    maxZoom: 18
}).addTo(map);

// Define your travel destinations
var destinations = [
    {
        name: "San Francisco, USA",
        lat: 37.7749,
        lng: -122.4194,
        visited: "2023"
    },
    {
        name: "Shenzhen, China",
        lat: 22.5429,
        lng: 114.0630,
        description: "Ain't noting like home",
    },
    {
        name: "Hong Kong, China",
        lat: 22.3193,
        lng: 114.1694,
    },
    {
        name: "Shanghai, China",
        lat: 31.2304,
        lng: 121.4737,
    },
    {
        name: "Kunming, China",
        lat: 25.0389,
        lng: 102.7180,
    },
    {
        name: "Xiamen, China",
        lat: 24.4798,
        lng: 118.0894,
    },
    {
        name: "Guilin, China",
        lat: 25.2742,
        lng: 110.2902,
    },
    {
        name: "Hengyang, China",
        lat: 26.8968,
        lng: 112.5857,
    },
    {
        name: "Chengdu, China",
        lat: 30.5728,
        lng: 104.0668,
    },
    {
        name: "Chongqing, China",
        lat: 29.5630,
        lng: 106.5516,
    },
    {
        name: "Wuhan, China",
        lat: 30.5928,
        lng: 114.3055,
    },
    {
        name: "Changsha, China",
        lat: 28.2282,
        lng: 112.9388,
    },
    {
        name: "Nanjing, China",
        lat: 32.0603,
        lng: 118.7969,
    },
    {
        name: "Guangzhou, China",
        lat: 23.1291,
        lng: 113.2644,
    },
    {
        name: "Tokyo, Japan",
        lat: 35.6895,
        lng: 139.6917,
    },
    {
        name: "Cebu City, Philippines",
        lat: 10.3157,
        lng: 123.8854,
    },
    {
        name: "Bali, Indonesia",
        lat: -8.4095,
        lng: 115.1889,
    },
    {
        name: "Maui, Hawaii, USA",
        lat: 20.7984,
        lng: -156.3319,
    },
    {
        name: "Anchorage, AK, USA",
        lat: 61.2181,
        lng: -149.9003,
    },
    {
        name: "Fairbanks, AK, USA",
        lat: 64.8378,
        lng: -147.7164,
    },
    {
        name: "San Jose, CA, USA",
        lat: 37.3382,
        lng: -121.8863,
    },
    {
        name: "Sacramento, CA, USA",
        lat: 38.5816,
        lng: -121.4944,
    },
    {
        name: "Los Angeles, CA, USA",
        lat: 34.0522,
        lng: -118.2437,
    },
    {
        name: "Seattle, WA, USA",
        lat: 47.6062,
        lng: -122.3321,
    },
    {
        name: "Yellowstone National Park, WY, USA",
        lat: 44.4280,
        lng: -110.5885,
    },
    {
        name: "Salt Lake City, UT, USA",
        lat: 40.7608,
        lng: -111.8910,
    },
    {
        name: "Sedona, AZ, USA",
        lat: 34.8697,
        lng: -111.7609,
    },
    {
        name: "Las Vegas, NV, USA",
        lat: 36.1699,
        lng: -115.1398,
    },
    {
        name: "Zion National Park, UT, USA",
        lat: 37.2982,
        lng: -113.0263,
        visited: "Mar 2023, May 2025"
    },
    {
        name: "Grand Canyon National Park, AZ, USA",
        lat: 36.1069,
        lng: -112.1129,
        visited: "May 2025"
    },
    {
        name: "Yosemite National Park, CA, USA",
        lat: 37.8651,
        lng: -119.5383,
    },
    {
        name: "Denver, CO, USA",
        lat: 39.7392,
        lng: -104.9903,
    },
    {
        name: "Chicago, IL, USA",
        lat: 41.8781,
        lng: -87.6298,
    },
    {
        name: "Champaign, IL, USA",
        lat: 40.1164,
        lng: -88.2434,
    },
    {
        name: "Ann Arbor, Michigan, USA",
        lat: 42.2808,
        lng: -83.7430,
    },
    {
        name: "Kewanna, Indiana, USA",
        lat: 41.0653,
        lng: -86.6219,
    },
    {
        name: "Orlando, FL, USA",
        lat: 28.5383,
        lng: -81.3792,
    },
    {
        name: "Washington, D.C., USA",
        lat: 38.9072,
        lng: -77.0369,
    },
    {
        name: "Brooklyn, NY, USA",
        lat: 40.6782,
        lng: -73.9442,
    },
    {
        name: "San Juan, Puerto Rico, USA",
        lat: 18.4655,
        lng: -66.1057,
    }
];

// Custom marker style - precise circle marker
var customIcon = L.divIcon({
    className: 'custom-marker',
    html: '<div class="marker-dot"></div>',
    iconSize: [12, 12],
    iconAnchor: [6, 6]
});

// Add markers for each destination at multiple world positions
destinations.forEach(function(dest) {
    var popupContent = `
        <div style="min-width: 200px;">
            <h3 style="margin: 0 0 10px 0; color: #2e3a59;">${dest.name}</h3>
            ${dest.description ? `<p style="margin: 0 0 8px 0; font-size: 14px;">${dest.description}</p>` : ''}
            ${dest.visited ? `<p style="margin: 0; font-size: 12px; color: #666; font-weight: bold;">Visited: ${dest.visited}</p>` : ''}
        </div>
    `;
    
    // Create markers at multiple world positions for continuous visibility
    for (var i = -1; i <= 1; i++) {
        var lng = dest.lng + (i * 360);
        var marker = L.marker([dest.lat, lng], {icon: customIcon}).addTo(map);
        marker.bindPopup(popupContent, {
            maxWidth: 250,
            className: 'custom-popup'
        });
    }
});
</script>

<style>
.custom-marker {
    cursor: pointer;
}

.marker-dot {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background-color: #ff6b6b;
    border: 2px solid white;
    box-shadow: 0 2px 6px rgba(0,0,0,0.3);
    transition: all 0.2s ease;
}

.marker-dot:hover {
    transform: scale(1.2);
    box-shadow: 0 3px 8px rgba(0,0,0,0.4);
}

.custom-popup .leaflet-popup-content-wrapper {
    border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}

.custom-popup .leaflet-popup-content {
    margin: 12px 16px;
}

.custom-popup .leaflet-popup-tip {
    background: white;
}

#travel-map {
    z-index: 1;
}

@media (max-width: 768px) {
    #travel-map {
        height: 300px;
        width: 95% !important;
        margin: 15px auto;
    }
}
</style>

## Travel Stats

- **Countries Visited**: 4/193
  <div class="progress-container">
    <div class="progress-bar" style="width: 2%;"></div>
  </div>
  <span class="progress-text">2% of 193 UN recognized countries</span>

- **Continents**: 2/7 (North America, Asia)
  <div class="progress-container">
    <div class="progress-bar" style="width: 28.6%;"></div>
  </div>
  <span class="progress-text">28.6% of 7 continents</span>

- **US States**: 14/50 (Alaska, Arizona, California, Colorado, Florida, Hawaii, Illinois, Indiana, Michigan, Nevada, New York, Utah, Washington, Wyoming)
  <div class="progress-container">
    <div class="progress-bar" style="width: 28%;"></div>
  </div>
  <span class="progress-text">28% complete</span>

- **US National Parks**: 7/63 (Yellowstone, Grand Canyon, Yosemite, Zion, Bryce Canyon, Rocky Mountain, Grand Teton)
  <div class="progress-container">
    <div class="progress-bar" style="width: 11.1%;"></div>
  </div>
  <span class="progress-text">11.1% complete</span>

<style>
.progress-container {
    width: 100%;
    height: 8px;
    background-color: #f0f0f0;
    border-radius: 4px;
    overflow: hidden;
    margin: 8px 0 4px 0;
    box-shadow: inset 0 1px 3px rgba(0,0,0,0.1);
}

.progress-bar {
    height: 100%;
    background-color: #ff6b6b;
    border-radius: 4px;
    transition: width 0.8s ease;
    box-shadow: 0 1px 2px rgba(0,0,0,0.2);
}

.progress-text {
    font-size: 0.85em;
    color: #666;
    font-style: italic;
    margin-left: 4px;
}

@media (max-width: 768px) {
    .progress-container {
        margin: 6px 0 3px 0;
    }
    
    .progress-text {
        font-size: 0.8em;
    }
}
</style>