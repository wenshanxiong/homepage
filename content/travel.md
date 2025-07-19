---
title: "Travel"
date: 2024-01-01
draft: false
---

# My Travel Adventures

Explore the places I've been to around the world! Click on the pins to learn more about each destination.

<div id="travel-map" style="height: 500px; width: 100%; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 10px rgba(0,0,0,0.1);"></div>

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<script>
// Initialize the map
var map = L.map('travel-map').setView([20, 0], 2);

// Add tile layer
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '© OpenStreetMap contributors',
    maxZoom: 18,
}).addTo(map);

// Define your travel destinations
var destinations = [
    {
        name: "San Francisco, USA",
        lat: 37.7749,
        lng: -122.4194,
        description: "The tech capital of the world! Loved the Golden Gate Bridge and Alcatraz.",
        visited: "2023"
    },
    {
        name: "Shenzhen, China",
        lat: 22.5429,
        lng: 114.0630,
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
    },
    {
        name: "Grand Canyon National Park, AZ, USA",
        lat: 36.1069,
        lng: -112.1129,
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
        name: "Brooklyn, NY, USA",
        lat: 40.6782,
        lng: -73.9442,
    }
];

// Custom marker style
var customIcon = L.divIcon({
    className: 'custom-marker',
    html: '📍',
    iconSize: [30, 30],
    iconAnchor: [15, 15]
});

// Add markers for each destination
destinations.forEach(function(dest) {
    var marker = L.marker([dest.lat, dest.lng], {icon: customIcon}).addTo(map);
    
    var popupContent = `
        <div style="min-width: 200px;">
            <h3 style="margin: 0 0 10px 0; color: #2e3a59;">${dest.name}</h3>
            <p style="margin: 0 0 8px 0; font-size: 14px;">${dest.description}</p>
            <p style="margin: 0; font-size: 12px; color: #666; font-weight: bold;">Visited: ${dest.visited}</p>
        </div>
    `;
    
    marker.bindPopup(popupContent, {
        maxWidth: 250,
        className: 'custom-popup'
    });
});
</script>

<style>
.custom-marker {
    font-size: 24px;
    text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
    cursor: pointer;
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
        height: 400px;
        margin: 15px 0;
    }
}
</style>

## Travel Stats

- **Countries Visited**: 5
- **Continents**: 4 (North America, Asia, Europe, Oceania)
- **Favorite Destination**: Tokyo, Japan 🇯🇵
- **Next on the List**: Iceland, New Zealand, and more of Europe!

## Travel Tips

Here are some things I've learned from my travels:

- Always carry a portable charger
- Learn basic phrases in the local language
- Try the street food (when it's safe!)
- Take more photos of people, not just places
- Pack light - you can always buy what you need

---

*Want to share your own travel stories? Feel free to reach out!* 