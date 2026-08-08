---
layout: single
title: Travel Log
permalink: /travel/
author_profile: true
---

<!-- External Dependencies -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<style>
  /* Base Container Resets */
  .stats-container {
    display: flex !important;
    flex-direction: row;
    gap: 15px;
    margin-bottom: 25px;
    flex-wrap: wrap;
    width: 100%;
    box-sizing: border-box;
  }
  .stat-card {
    flex: 1 1 200px;
    min-width: 140px;
    background: linear-gradient(135deg, #007bff, #0056b3);
    color: #ffffff !important;
    padding: 20px;
    border-radius: 12px;
    text-align: center;
    cursor: pointer;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    box-sizing: border-box;
  }
  .stat-card:hover, .stat-card:active {
    transform: translateY(-3px);
    box-shadow: 0 6px 12px rgba(0,0,0,0.15);
  }
  .stat-card h2 {
    margin: 0 !important;
    font-size: 2.5em !important;
    font-weight: 700;
    color: #ffffff !important;
    border: none !important;
  }
  .stat-card p {
    margin: 5px 0 0 0 !important;
    font-size: 1.1em;
    font-weight: 500;
    color: #ffffff !important;
  }
  /* Modals */
  .modal-overlay {
    display: none;
    position: fixed;
    z-index: 9999;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.6);
    backdrop-filter: blur(4px);
    justify-content: center;
    align-items: center;
  }
  .modal-content {
    background-color: #fff;
    padding: 25px;
    border-radius: 12px;
    width: 90%;
    max-width: 550px;
    max-height: 80vh;
    overflow-y: auto;
    position: relative;
    box-shadow: 0 10px 25px rgba(0,0,0,0.2);
    color: #333;
  }
  .modal-close {
    position: absolute;
    top: 15px;
    right: 20px;
    font-size: 28px;
    font-weight: bold;
    color: #333;
    cursor: pointer;
    line-height: 1;
  }
  .modal-close:hover { color: #dc3545; }
  .modal-content h3 {
    margin-top: 0;
    border-bottom: 2px solid #eee;
    padding-bottom: 10px;
    color: #333;
  }
  .modal-content h4 {
    margin: 20px 0 10px 0;
    font-size: 1.1em;
    color: #0056b3;
    border-bottom: 1px solid #f0f0f0;
    padding-bottom: 5px;
  }
  .modal-list {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  .modal-list li {
    padding: 6px 0;
    font-size: 0.95em;
  }
  .modal-list strong { color: #333; }
  .unesco-link {
    color: #198754;
    text-decoration: none;
    font-weight: 500;
  }
  .unesco-link:hover { text-decoration: underline; }
  /* Map Container */
  #map {
    height: 400px;
    width: 100%;
    margin-bottom: 30px;
    border-radius: 8px;
    z-index: 1;
    position: relative;
  }
  @media (max-width: 600px) { #map { height: 350px; } }
  /* Filter Buttons & Timeline */
  .filter-container {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
    overflow-x: auto;
    padding-bottom: 10px;
  }
  .filter-btn {
    padding: 8px 16px;
    border: 1px solid #ccc;
    border-radius: 20px;
    background-color: #f8f9fa;
    cursor: pointer;
    white-space: nowrap;
    transition: all 0.2s ease;
  }
  .filter-btn.active, .filter-btn:hover {
    background-color: #007bff;
    color: white;
    border-color: #007bff;
  }
  .trip-card {
    border-left: 4px solid #ddd;
    padding: 10px 15px;
    margin-bottom: 20px;
    background: #fafafa;
    border-radius: 0 8px 8px 0;
  }
  .trip-year-divider {
    border-top: 3px solid #333;
    margin: 30px 0 20px 0;
    padding-top: 10px;
    font-size: 1.5em;
    font-weight: bold;
  }
  .badge {
    display: inline-block;
    padding: 4px 8px;
    border-radius: 4px;
    font-size: 0.85em;
    font-weight: bold;
    margin-bottom: 8px;
    color: white;
  }
  .badge-intl { background-color: #dc3545; }
  .badge-dom { background-color: #0d6efd; }
  .badge-local { background-color: #198754; }
</style>

<div class="stats-container">
  <div class="stat-card" onclick="openModal('countries-modal')">
    <h2>28</h2>
    <p>Countries Visited</p>
  </div>
  <div class="stat-card" onclick="openModal('unesco-modal')">
    <h2>47</h2>
    <p>UNESCO Sites</p>
  </div>
</div>

<div id="countries-modal" class="modal-overlay" onclick="closeModalOnOutsideClick(event, 'countries-modal')">
  <div class="modal-content">
    <span class="modal-close" onclick="closeModal('countries-modal')">&times;</span>
    <h3>Countries Visited (28)</h3>
    <h4>🌍 Europe (15)</h4>
    <ul class="modal-list" style="display: flex; flex-wrap: wrap; gap: 10px;">
      <li style="width: 45%;">🇦🇹 Austria</li>
      <li style="width: 45%;">🇭🇷 Croatia</li>
      <li style="width: 45%;">🇫🇷 France</li>
      <li style="width: 45%;">🇩🇪 Germany</li>
      <li style="width: 45%;">🇬🇷 Greece</li>
      <li style="width: 45%;">🇮🇸 Iceland</li>
      <li style="width: 45%;">🇮🇹 Italy</li>
      <li style="width: 45%;">🇳🇱 Netherlands</li>
      <li style="width: 45%;">🇳🇴 Norway</li>
      <li style="width: 45%;">🇵🇹 Portugal</li>
      <li style="width: 45%;">🇪🇸 Spain</li>
      <li style="width: 45%;">🇨🇭 Switzerland</li>
      <li style="width: 45%;">🇹🇷 Türkiye</li>
      <li style="width: 45%;">🇬🇧 United Kingdom</li>
      <li style="width: 45%;">🇻🇦 Vatican City</li>
    </ul>
    <h4>🌎 North America (4)</h4>
    <ul class="modal-list" style="display: flex; flex-wrap: wrap; gap: 10px;">
      <li style="width: 45%;">🇧🇸 Bahamas</li>
      <li style="width: 45%;">🇨🇦 Canada</li>
      <li style="width: 45%;">🇲🇽 Mexico</li>
      <li style="width: 45%;">🇺🇸 United States</li>
    </ul>
    <h4>🌏 Asia (4)</h4>
    <ul class="modal-list" style="display: flex; flex-wrap: wrap; gap: 10px;">
      <li style="width: 45%;">🇮🇳 India</li>
      <li style="width: 45%;">🇮🇩 Indonesia</li>
      <li style="width: 45%;">🇹🇭 Thailand</li>
      <li style="width: 45%;">🇦🇪 United Arab Emirates</li>
    </ul>
    <h4>🌎 South America (3)</h4>
    <ul class="modal-list" style="display: flex; flex-wrap: wrap; gap: 10px;">
      <li style="width: 45%;">🇪🇨 Ecuador</li>
      <li style="width: 45%;">🇵🇪 Peru</li>
      <li style="width: 45%;">🇨🇴 Colombia</li>
    </ul>
    <h4>🐪 Africa (1)</h4>
    <ul class="modal-list" style="display: flex; flex-wrap: wrap; gap: 10px;">
      <li style="width: 45%;">🇪🇬 Egypt</li>
    </ul>
  </div>
</div>

<div id="unesco-modal" class="modal-overlay" onclick="closeModalOnOutsideClick(event, 'unesco-modal')">
  <div class="modal-content">
    <span class="modal-close" onclick="closeModal('unesco-modal')">&times;</span>
    <h3>UNESCO World Heritage Sites (47)</h3>
    <h4>🌍 Europe (28 Sites)</h4>
    <ul class="modal-list">
      <li><strong>Austria:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/784" target="_blank">Historic Salzburg</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/806" target="_blank">Hallstatt-Dachstein</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/1033" target="_blank">Historic Vienna</a></li>
      <li><strong>Croatia:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/98" target="_blank">Plitvice Lakes</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/97" target="_blank">Historical Split</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/95" target="_blank">Old City of Dubrovnik</a></li>
      <li><strong>France:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/600" target="_blank">Paris, Banks of the Seine</a></li>
      <li><strong>Greece:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/404" target="_blank">Acropolis, Athens</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/455" target="_blank">Meteora</a></li>
      <li><strong>Hungary:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/400" target="_blank">Budapest (Banks of Danube/Buda Castle)</a></li>
      <li><strong>Italy:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/394" target="_blank">Venice</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/174" target="_blank">Historic Florence</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/395" target="_blank">Piazza del Duomo, Pisa</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/91" target="_blank">Historic Rome</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/826" target="_blank">Cinque Terre</a></li>
      <li><strong>Netherlands:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/1349" target="_blank">Canal Ring Area of Amsterdam</a></li>
      <li><strong>Norway:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/1195" target="_blank">Geirangerfjord</a></li>
      <li><strong>Portugal:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/263" target="_blank">Tower of Belém, Lisbon</a></li>
      <li><strong>Spain:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/320" target="_blank">Works of Antoni Gaudí</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/383" target="_blank">Seville Cathedral/Alcázar</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/314" target="_blank">Alhambra, Granada</a></li>
      <li><strong>Switzerland:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/267" target="_blank">Old City of Bern</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/1037" target="_blank">Swiss Alps Jungfrau-Aletsch</a></li>
      <li><strong>Türkiye:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/356" target="_blank">Historic Istanbul</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/357" target="_blank">Göreme / Cappadocia</a></li>
      <li><strong>United Kingdom:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/728" target="_blank">Old/New Towns of Edinburgh</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/488" target="_blank">Tower of London</a></li>
      <li><strong>Vatican City:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/286" target="_blank">Vatican City</a></li>
    </ul>
    <h4>🌎 North America (6 Sites)</h4>
    <ul class="modal-list">
      <li><strong>Canada:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/304" target="_blank">Canadian Rocky Mountain Parks</a></li>
      <li><strong>United States:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/259" target="_blank">Great Smoky Mountains</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/308" target="_blank">Yosemite</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/409" target="_blank">Hawaii Volcanoes</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/75" target="_blank">Grand Canyon</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/28" target="_blank">Yellowstone</a></li>
    </ul>
    <h4>🌎 South America (5 Sites)</h4>
    <ul class="modal-list">
      <li><strong>Ecuador:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/2" target="_blank">City of Quito</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/1" target="_blank">Galápagos Islands</a></li>
      <li><strong>Peru:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/273" target="_blank">City of Cuzco</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/274" target="_blank">Machu Picchu</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/500" target="_blank">Historic Lima</a></li>
    </ul>
    <h4>🐪 Africa (4 Sites)</h4>
    <ul class="modal-list">
      <li><strong>Egypt:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/86" target="_blank">Memphis/Giza</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/87" target="_blank">Ancient Thebes (Luxor)</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/88" target="_blank">Nubian Monuments (Abu Simbel)</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/89" target="_blank">Historic Cairo</a></li>
    </ul>
    <h4>🌏 Asia (4 Sites)</h4>
    <ul class="modal-list">
      <li><strong>India:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/231" target="_blank">Red Fort Complex</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/232" target="_blank">Humayun's Tomb</a>, <a class="unesco-link" href="https://whc.unesco.org/en/list/233" target="_blank">Qutb Minar</a></li>
      <li><strong>Indonesia:</strong> <a class="unesco-link" href="https://whc.unesco.org/en/list/1194" target="_blank">Cultural Landscape of Bali</a></li>
    </ul>
  </div>
</div>

<h2>Travel Map</h2>
<div id="map"></div>

<h2>Trip Logs</h2>

<div class="filter-container">
  <button class="filter-btn active" onclick="filterTrips(event, 'All')">All Trips</button>
  <button class="filter-btn" onclick="filterTrips(event, 'International')">🌍 International</button>
  <button class="filter-btn" onclick="filterTrips(event, 'Domestic')">✈️ Domestic</button>
  <button class="filter-btn" onclick="filterTrips(event, 'Local')">🚗 Local</button>
</div>

<div id="timeline">
  <div class="trip-year-divider">2026</div>
  <div class="trip-card" data-type="International">
    <span class="badge badge-intl">International</span><br>
    <strong>United States & The Bahamas:</strong> Miami Beach, Bahamas, Buffalo, Cheektowaga, Niagara Falls<br>
    <em>Jun 14, 2026 - Jun 21, 2026</em><br>
    🧑‍🤝‍🧑 Onam, Rohit, Family
  </div>
  <div class="trip-card" data-type="Domestic">
    <span class="badge badge-dom">Domestic</span><br>
    <strong>United States:</strong> Bellevue, Seattle<br>
    <em>Jun 8, 2026 - Jun 11, 2026</em><br>
    🧑‍🤝‍🧑 Onam
  </div>
</div>

<script>
  function openModal(modalId) {
    document.getElementById(modalId).style.display = 'flex';
    document.body.style.overflow = 'hidden';
  }
  function closeModal(modalId) {
    document.getElementById(modalId).style.display = 'none';
    document.body.style.overflow = 'auto';
  }
  function closeModalOnOutsideClick(event, modalId) {
    if (event.target.id === modalId) {
      closeModal(modalId);
    }
  }
  function filterTrips(event, type) {
    document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.remove('active'));
    event.currentTarget.classList.add('active');
    const trips = document.querySelectorAll('.trip-card');
    trips.forEach(trip => {
      if (type === 'All' || trip.getAttribute('data-type') === type) {
        trip.style.display = 'block';
      } else {
        trip.style.display = 'none';
      }
    });
  }
  function initMap() {
    if (typeof L === 'undefined') {
      setTimeout(initMap, 100);
      return;
    }
    const mapContainer = document.getElementById('map');
    if (!mapContainer) return;
    const map = L.map('map').setView([20, 0], 2);
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      maxZoom: 18,
      attribution: '© OpenStreetMap contributors'
    }).addTo(map);
    const travelData = [
      { name: "Seattle, WA", coords: [47.6062, -122.3321], continent: "North America", year: "Multiple" },
      { name: "New York, NY", coords: [40.7128, -74.0060], continent: "North America", year: "Multiple" },
      { name: "Las Vegas, NV", coords: [36.1699, -115.1398], continent: "North America", year: "Multiple" },
      { name: "San Diego, CA", coords: [32.7157, -117.1611], continent: "North America", year: "Multiple" },
      { name: "Miami, FL", coords: [25.7617, -80.1918], continent: "North America", year: "Multiple" },
      { name: "Chicago, IL", coords: [41.8781, -87.6298], continent: "North America", year: "2015" },
      { name: "Fairbanks, AK", coords: [64.8378, -147.7164], continent: "North America", year: "2023" },
      { name: "Honolulu, HI", coords: [21.3069, -157.8583], continent: "North America", year: "2023" },
      { name: "Grand Canyon, AZ", coords: [36.0544, -112.1401], continent: "North America", year: "2018" },
      { name: "Yellowstone NP, WY", coords: [44.4280, -110.5885], continent: "North America", year: "2015" },
      { name: "Yosemite NP, CA", coords: [37.8651, -119.5383], continent: "North America", year: "2022" },
      { name: "Vancouver, Canada", coords: [49.2827, -123.1207], continent: "North America", year: "Multiple" },
      { name: "Banff, Canada", coords: [51.1784, -115.5708], continent: "North America", year: "2021" },
      { name: "Cancun, Mexico", coords: [21.1619, -86.8515], continent: "North America", year: "Multiple" },
      { name: "Cabo San Lucas, Mexico", coords: [22.8905, -109.9167], continent: "North America", year: "2024" },
      { name: "Bahamas", coords: [25.0343, -77.3963], continent: "North America", year: "2026" },
      { name: "Cusco, Peru", coords: [-13.5320, -71.9675], continent: "South America", year: "2022" },
      { name: "Lima, Peru", coords: [-12.0464, -77.0428], continent: "South America", year: "2022" },
      { name: "Quito, Ecuador", coords: [-0.1807, -78.4678], continent: "South America", year: "2025" },
      { name: "Galápagos Islands", coords: [-0.8293, -90.9821], continent: "South America", year: "2025" },
      { name: "London, UK", coords: [51.5074, -0.1278], continent: "Europe", year: "2023" },
      { name: "Edinburgh, UK", coords: [55.9533, -3.1883], continent: "Europe", year: "2023" },
      { name: "Paris, France", coords: [48.8566, 2.3522], continent: "Europe", year: "2018" },
      { name: "Barcelona, Spain", coords: [41.3851, 2.1734], continent: "Europe", year: "Multiple" },
      { name: "Lisbon, Portugal", coords: [38.7223, -9.1393], continent: "Europe", year: "2019" },
      { name: "Amsterdam, Netherlands", coords: [52.3676, 4.9041], continent: "Europe", year: "2022" },
      { name: "Rome, Italy", coords: [41.9028, 12.4964], continent: "Europe", year: "2016" },
      { name: "Venice, Italy", coords: [45.4408, 12.3155], continent: "Europe", year: "2016" },
      { name: "Florence, Italy", coords: [43.7696, 11.2558], continent: "Europe", year: "2016" },
      { name: "Athens, Greece", coords: [37.9838, 23.7275], continent: "Europe", year: "2022" },
      { name: "Munich, Germany", coords: [48.1351, 11.5820], continent: "Europe", year: "2024" },
      { name: "Vienna, Austria", coords: [48.2082, 16.3738], continent: "Europe", year: "2024" },
      { name: "Salzburg, Austria", coords: [47.8095, 13.0550], continent: "Europe", year: "2024" },
      { name: "Dubrovnik, Croatia", coords: [42.6507, 18.0944], continent: "Europe", year: "2024" },
      { name: "Split, Croatia", coords: [43.5081, 16.4402], continent: "Europe", year: "2024" },
      { name: "Reykjavik, Iceland", coords: [64.1466, -21.9426], continent: "Europe", year: "2024" },
      { name: "Oslo, Norway", coords: [59.9139, 10.7522], continent: "Europe", year: "2025" },
      { name: "Bern, Switzerland", coords: [46.9480, 7.4474], continent: "Europe", year: "2018" },
      { name: "Cairo, Egypt", coords: [30.0444, 31.2357], continent: "Africa", year: "2023" },
      { name: "Luxor, Egypt", coords: [25.6872, 32.6396], continent: "Africa", year: "2023" },
      { name: "Abu Simbel, Egypt", coords: [22.3372, 31.6258], continent: "Africa", year: "2023" },
      { name: "Dubai, UAE", coords: [25.2048, 55.2708], continent: "Asia", year: "2013" },
      { name: "Istanbul, Türkiye", coords: [41.0082, 28.9784], continent: "Asia", year: "Multiple" },
      { name: "Cappadocia, Türkiye", coords: [38.6431, 34.8303], continent: "Asia", year: "Multiple" },
      { name: "Delhi, India", coords: [28.7041, 77.1025], continent: "Asia", year: "Multiple" },
      { name: "Kolkata, India", coords: [22.5726, 88.3639], continent: "Asia", year: "Multiple" },
      { name: "Chennai, India", coords: [13.0827, 80.2707], continent: "Asia", year: "Multiple" },
      { name: "Mumbai, India", coords: [19.0760, 72.8777], continent: "Asia", year: "2018" },
      { name: "Bangalore, India", coords: [12.9716, 77.5946], continent: "Asia", year: "Multiple" },
      { name: "Patna, India", coords: [25.5941, 85.1376], continent: "Asia", year: "Multiple" },
      { name: "Phuket, Thailand", coords: [7.8804, 98.3923], continent: "Asia", year: "2025" },
      { name: "Bali, Indonesia", coords: [-8.4095, 115.1889], continent: "Asia", year: "2017" }
    ];
    function getMarkerColor(continent) {
      switch(continent) {
        case 'Europe': return '#6f42c1';
        case 'North America': return '#0d6efd';
        case 'South America': return '#198754';
        case 'Asia': return '#fd7e14';
        case 'Africa': return '#ffc107';
        default: return '#6c757d';
      }
    }
    travelData.forEach(function(location) {
      L.circleMarker(location.coords, {
        radius: 6,
        fillColor: getMarkerColor(location.continent),
        color: "#ffffff",
        weight: 1.5,
        opacity: 1,
        fillOpacity: 0.85
      })
      .addTo(map)
      .bindPopup(`<b>${location.name}</b><br><span style="color:${getMarkerColor(location.continent)}"><i>${location.continent}</i></span><br><small style="color:#555;">Visited: <b>${location.year}</b></small>`);
    });
    setTimeout(() => { map.invalidateSize(); }, 200);
  }
  if (document.readyState === "loading") {
    document.addEventListener("DOMContentLoaded", initMap);
  } else {
    initMap();
  }
</script>
