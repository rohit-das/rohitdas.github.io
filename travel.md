---
layout: page
title: Travel Log
permalink: /travel/
---

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<link rel="stylesheet" href="https://unpkg.com/leaflet.markercluster@1.5.3/dist/MarkerCluster.css" />
<link rel="stylesheet" href="https://unpkg.com/leaflet.markercluster@1.5.3/dist/MarkerCluster.Default.css" />

<style>
  /* Dashboard Stats Grid */
  .travel-stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 15px;
    margin-bottom: 25px;
  }
  .stat-card {
    background: var(--background-secondary, #f8f9fa);
    border: 1px solid var(--border-color, #e9ecef);
    border-radius: 10px;
    padding: 16px;
    text-align: center;
    box-shadow: 0 2px 6px rgba(0,0,0,0.04);
  }
  .stat-card .stat-number {
    font-size: 1.8rem;
    font-weight: bold;
    color: #0366d6;
    margin-bottom: 4px;
  }
  .stat-card .stat-label {
    font-size: 0.88rem;
    color: #6a737d;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  /* Interactive Map Styling */
  #travel-map {
    height: 450px;
    width: 100%;
    border-radius: 12px;
    border: 1px solid #d0d7de;
    margin-bottom: 30px;
    z-index: 1;
  }

  /* Filter Buttons Styling */
  .filter-container {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    margin-bottom: 25px;
  }
  .filter-btn {
    padding: 8px 16px;
    border: 1px solid #d0d7de;
    border-radius: 20px;
    background: #ffffff;
    color: #24292e;
    font-weight: 600;
    font-size: 0.9rem;
    cursor: pointer;
    transition: all 0.2s ease;
  }
  .filter-btn:hover {
    background: #f3f4f6;
  }
  .filter-btn.active {
    background: #0366d6;
    color: #ffffff;
    border-color: #0366d6;
  }

  /* Trip Cards Styling */
  .trip-card {
    border-left: 4px solid #d0d7de;
    padding: 12px 18px;
    margin-bottom: 18px;
    background: var(--card-bg, #ffffff);
    border-radius: 0 8px 8px 0;
    box-shadow: 0 1px 4px rgba(0,0,0,0.05);
    transition: transform 0.15s ease;
  }
  .trip-card:hover {
    transform: translateX(4px);
  }
  .trip-card[data-category="international"] { border-left-color: #d9534f; }
  .trip-card[data-category="domestic"] { border-left-color: #0275d8; }
  .trip-card[data-category="regional"] { border-left-color: #5cb85c; }

  .trip-badge {
    display: inline-block;
    padding: 3px 8px;
    border-radius: 12px;
    font-size: 0.75rem;
    font-weight: bold;
    color: white;
    margin-left: 8px;
  }
  .badge-international { background-color: #d9534f; }
  .badge-domestic { background-color: #0275d8; }
  .badge-regional { background-color: #5cb85c; }

  .photo-link {
    display: inline-flex;
    align-items: center;
    gap: 4px;
    font-size: 0.82rem;
    margin-top: 6px;
    color: #0366d6;
    text-decoration: none;
    font-weight: 500;
  }
  .photo-link:hover { text-decoration: underline; }
</style>

<div class="travel-stats-grid">
  <div class="stat-card">
    <div class="stat-number">25+</div>
    <div class="stat-label">Countries Visited</div>
  </div>
  <div class="stat-card">
    <div class="stat-number">15+</div>
    <div class="stat-label">US States Visited</div>
  </div>
  <div class="stat-card">
    <div class="stat-number">65+</div>
    <div class="stat-label">Trips Logged</div>
  </div>
  <div class="stat-card">
    <div class="stat-number">5</div>
    <div class="stat-label">Continents Explored</div>
  </div>
</div>

<div id="travel-map"></div>

<div class="filter-container">
  <button class="filter-btn active" onclick="filterTrips('all')">All Trips</button>
  <button class="filter-btn" onclick="filterTrips('international')">🌍 International</button>
  <button class="filter-btn" onclick="filterTrips('domestic')">✈️ Domestic US</button>
  <button class="filter-btn" onclick="filterTrips('regional')">🚗 Regional Getaways</button>
</div>

---

## 🗓️ Chronological Travel History

<div id="trip-list">

  <div class="trip-card" data-category="international">
    <strong>Nov 12, 2026 – Dec 3, 2026</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Tokyo, Japan & Seoul, South Korea<br/>
    <strong>Details:</strong> Flight (United Airlines via Chase Travel)<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Jun 19, 2026 – Jun 21, 2026</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Buffalo, Cheektowaga & Niagara Falls, NY<br/>
    <strong>Details:</strong> Accommodation & Car Rental (National / Expedia)<br/>
    <strong>Companions:</strong> Onam Bharti, Rohit Das, Anusha, Meera
  </div>

  <div class="trip-card" data-category="international">
    <strong>Jun 14, 2026 – Jun 18, 2026</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Miami Beach, FL & CocoCay, The Bahamas<br/>
    <strong>Details:</strong> Flight, Cruise & Hotel Stay<br/>
    <strong>Companions:</strong> Rohit Das, Onam Ani, Meera
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Jun 8, 2026 – Jun 11, 2026</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Bellevue & Seattle, WA<br/>
    <strong>Details:</strong> Flight & Hotel (Alaska Airlines & Hyatt Regency)<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>May 16, 2026 – May 17, 2026</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Okaloosa Island & Eglin AFB, FL<br/>
    <strong>Details:</strong> Photo Log<br/>
    <strong>Companions:</strong> Solo
  </div>

  <div class="trip-card" data-category="international">
    <strong>Dec 21, 2025 – Dec 30, 2025</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Quito, San Cristóbal Island, Puerto Ayora, Baltra & Napo (Amazon), Ecuador<br/>
    <strong>Details:</strong> Galápagos Islands Expedition & Amazon Rainforest Tour<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das<br/>
    <a href="https://photos.google.com" target="_blank" class="photo-link">📸 View Photo Album</a>
  </div>

  <div class="trip-card" data-category="international">
    <strong>Dec 12, 2025 – Dec 14, 2025</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Delhi, India<br/>
    <strong>Details:</strong> Flight (Air Canada / Air India)<br/>
    <strong>Companions:</strong> Anusha Gupta
  </div>

  <div class="trip-card" data-category="international">
    <strong>Aug 22, 2025 – Sep 1, 2025</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Bergen, Ålesund, Geiranger, Aurlandsvangen, Åndalsnes & Oslo, Norway<br/>
    <strong>Details:</strong> Flight (United / Lufthansa) & Norwegian Fjords Airbnb Tour<br/>
    <strong>Companions:</strong> Onam Bharti, Rohit Das + 2 Guests<br/>
    <a href="https://photos.google.com" target="_blank" class="photo-link">📸 View Photo Album</a>
  </div>

  <div class="trip-card" data-category="international">
    <strong>Jul 27, 2025 – Jul 28, 2025</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Kolkata, India (via Delhi)<br/>
    <strong>Details:</strong> Flight (Air India)<br/>
    <strong>Companions:</strong> Shambhu Nath Das
  </div>

  <div class="trip-card" data-category="regional">
    <strong>Jun 29, 2025 – Jul 5, 2025</strong> <span class="trip-badge badge-regional">🚗 Regional</span><br/>
    <strong>Destination:</strong> Sierra Nevada, June Lake, Mammoth Lakes & Strawberry, CA<br/>
    <strong>Details:</strong> Eastern Sierra Mountain Road Trip<br/>
    <strong>Companions:</strong> S N Das, Onam Bharti, Anusha, Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>May 10, 2025</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Red Rocks Park & Amphitheatre, CO<br/>
    <strong>Details:</strong> Photo Log<br/>
    <strong>Companions:</strong> Solo
  </div>

  <div class="trip-card" data-category="regional">
    <strong>Apr 5, 2025</strong> <span class="trip-badge badge-regional">🚗 Regional</span><br/>
    <strong>Destination:</strong> Knights Ferry, CA<br/>
    <strong>Details:</strong> Day Trip & Covered Bridge Visit<br/>
    <strong>Companions:</strong> Onam Bharti
  </div>

  <div class="trip-card" data-category="international">
    <strong>Mar 19, 2025 – Mar 23, 2025</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Ao Nang, Phuket & Rawai, Thailand<br/>
    <strong>Details:</strong> Tropical Beach Getaway & Resort Stay<br/>
    <strong>Companions:</strong> Onam Bharti, Rohit Das, Meera
  </div>

  <div class="trip-card" data-category="international">
    <strong>Mar 1, 2025 – Apr 2, 2025</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Delhi, India<br/>
    <strong>Details:</strong> Flight (Qatar Airways)<br/>
    <strong>Companions:</strong> Onam Bharti
  </div>

  <div class="trip-card" data-category="international">
    <strong>Dec 21, 2024 – Dec 24, 2024</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Cabo San Lucas, Baja California Sur, Mexico<br/>
    <strong>Details:</strong> Coastal Resort Getaway<br/>
    <strong>Companions:</strong> Onam Bharti
  </div>

  <div class="trip-card" data-category="international">
    <strong>Oct 18, 2024 – Oct 19, 2024</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Barcelona, Spain<br/>
    <strong>Details:</strong> Flight (Air Canada)<br/>
    <strong>Companions:</strong> Onam Bharti
  </div>

  <div class="trip-card" data-category="international">
    <strong>Aug 24, 2024 – Sep 2, 2024</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Reykjavik, Reynisfjara, Múlaþing, Þingeyjarsveit & Siglufjörður, Iceland<br/>
    <strong>Details:</strong> Ring Road Expedition & Flight (Delta Air Lines)<br/>
    <strong>Companions:</strong> Rohit Das & Onam Bharti<br/>
    <a href="https://photos.google.com" target="_blank" class="photo-link">📸 View Photo Album</a>
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>May 19, 2024 – May 21, 2024</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Seattle & Bellevue, WA<br/>
    <strong>Details:</strong> Flight & Hotel (Alaska/Delta & Hyatt Regency)<br/>
    <strong>Companions:</strong> Onam Bharti
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Apr 21, 2024 – Apr 26, 2024</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Seattle, WA & Great Smoky Mountains NP / Knoxville, TN<br/>
    <strong>Details:</strong> National Park Trip & Flight (Delta)<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Mar 29, 2024 – Apr 12, 2024</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Munich (Germany) | Salzburg, Hallstatt, Vienna (Austria) | Split, Plitvice Lakes, Dubrovnik (Croatia)<br/>
    <strong>Details:</strong> Central & Southeastern European Multi-Country Tour<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Dec 24, 2023 – Dec 30, 2023</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Honolulu, Waimanalo & Kaneohe, Oahu, HI<br/>
    <strong>Details:</strong> Flight (United) & Oahu Island Tour<br/>
    <strong>Companions:</strong> Onam Bharti, Anusha Gupta & Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Nov 19, 2023 – Nov 25, 2023</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Giza, Cairo, Abu Simbel, Aswan, Luxor & Hurghada, Egypt<br/>
    <strong>Details:</strong> Nile Expedition, Ancient Pyramids & Red Sea Tour<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das<br/>
    <a href="https://photos.google.com" target="_blank" class="photo-link">📸 View Photo Album</a>
  </div>

  <div class="trip-card" data-category="international">
    <strong>Jul 2, 2023 – Jul 8, 2023</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Edinburgh (Scotland) | London & Cotswolds (United Kingdom)<br/>
    <strong>Details:</strong> UK & Scottish Highlands Tour<br/>
    <strong>Companions:</strong> Rohit Das & Onam Bharti
  </div>

  <div class="trip-card" data-category="regional">
    <strong>May 27, 2023 – May 29, 2023</strong> <span class="trip-badge badge-regional">🚗 Regional</span><br/>
    <strong>Destination:</strong> Fort Bragg & Navarro River Redwoods, CA<br/>
    <strong>Details:</strong> Northern California Mendocino Coast Road Trip<br/>
    <strong>Companions:</strong> Onam Bharti, Rohit Das, Dhruvil, Dhwani
  </div>

  <div class="trip-card" data-category="international">
    <strong>Mar 10, 2023 – Apr 2, 2023</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Istanbul & Cappadocia (Türkiye) & Delhi (India)<br/>
    <strong>Details:</strong> Flight (Turkish Airlines) & Cave Hotel Accommodation<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Feb 17, 2023 – Feb 20, 2023</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Anchorage & Fairbanks, Alaska<br/>
    <strong>Details:</strong> Winter Northern Lights Getaway<br/>
    <strong>Companions:</strong> Dhwani, Dhruvil, Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="regional">
    <strong>Dec 24, 2022</strong> <span class="trip-badge badge-regional">🚗 Regional</span><br/>
    <strong>Destination:</strong> Dorrington, Sierra Nevada, CA<br/>
    <strong>Details:</strong> Winter Mountain Cabin Trip<br/>
    <strong>Companions:</strong> Aparna, JP, Neha Vatsyayan
  </div>

  <div class="trip-card" data-category="international">
    <strong>Nov 21, 2022 – Nov 29, 2022</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Cusco, Machu Picchu & Lima, Peru<br/>
    <strong>Details:</strong> Ancient Inca Trail Exploration & Coastal Lima Stay<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Jul 29, 2022 – Jul 30, 2022</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Las Vegas, NV & Zion National Park, UT<br/>
    <strong>Details:</strong> Southwest National Park Getaway<br/>
    <strong>Companions:</strong> Meera & Onam Bharti
  </div>

  <div class="trip-card" data-category="international">
    <strong>Jun 17, 2022 – Aug 27, 2022</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> San Francisco <-> Delhi, India<br/>
    <strong>Details:</strong> Flight (Air India via Travelopod)<br/>
    <strong>Companions:</strong> Meera Devi & Tarun Kumar
  </div>

  <div class="trip-card" data-category="international">
    <strong>Apr 17, 2022 – Apr 27, 2022</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Athens, Meteora & Santorini (Greece) | Amsterdam (Netherlands)<br/>
    <strong>Details:</strong> Greek Islands Hopping & Dutch Canals Tour<br/>
    <strong>Companions:</strong> Rohit Das & Onam Bharti
  </div>

  <div class="trip-card" data-category="regional">
    <strong>Feb 19, 2022 – Feb 20, 2022</strong> <span class="trip-badge badge-regional">🚗 Regional</span><br/>
    <strong>Destination:</strong> Yosemite National Park, CA<br/>
    <strong>Details:</strong> Winter National Park Weekend<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Nov 21, 2021 – Nov 28, 2021</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Puerto Vallarta & Boca de Tomatlan, Mexico<br/>
    <strong>Details:</strong> Flight & Hotel Package (Sheraton Buganvilias Resort)<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="regional">
    <strong>Oct 30, 2021 – Oct 31, 2021</strong> <span class="trip-badge badge-regional">🚗 Regional</span><br/>
    <strong>Destination:</strong> Santa Ynez Valley, CA<br/>
    <strong>Details:</strong> Central Coast Wine Country Weekend<br/>
    <strong>Companions:</strong> Rohit, Sumedha, Neha, Siddhartha, Sutapa
  </div>

  <div class="trip-card" data-category="international">
    <strong>Aug 20, 2021 – Aug 29, 2021</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Calgary, Banff NP, Jasper NP, Lake Louise & Vancouver, Canada<br/>
    <strong>Details:</strong> Canadian Rockies Road Trip & Flight (WestJet)<br/>
    <strong>Companions:</strong> Rohit Das & Onam Bharti
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Mar 21, 2021 – Mar 26, 2021</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Big Island (Volcano, Hilo, Kona), HI<br/>
    <strong>Details:</strong> Hawaii Island Road Trip<br/>
    <strong>Companions:</strong> Rohit Das & Onam Bharti
  </div>

  <div class="trip-card" data-category="regional">
    <strong>Sep 3, 2020 – Sep 7, 2020</strong> <span class="trip-badge badge-regional">🚗 Regional</span><br/>
    <strong>Destination:</strong> Lakehead, CA & Eugene / McKenzie River, OR<br/>
    <strong>Details:</strong> Pacific Northwest River Retreat<br/>
    <strong>Companions:</strong> Onam Bharti, Rohit Das, Siddhartha Datta, Sutapa Dey
  </div>

  <div class="trip-card" data-category="international">
    <strong>Mar 5, 2020 – Mar 18, 2020</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Kolkata & Bengaluru, India (via Dubai)<br/>
    <strong>Details:</strong> Flight (Emirates Air)<br/>
    <strong>Companions:</strong> Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Feb 8, 2020 – Feb 17, 2020</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Cancun, Mexico & Miami Beach, FL<br/>
    <strong>Details:</strong> Flight & Resort Stay (InterContinental)<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Dec 1, 2019</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Pahrump, NV<br/>
    <strong>Details:</strong> Day Trip<br/>
    <strong>Companions:</strong> Rohit Das
  </div>

  <div class="trip-card" data-category="regional">
    <strong>Aug 31, 2019 – Sep 2, 2019</strong> <span class="trip-badge badge-regional">🚗 Regional</span><br/>
    <strong>Destination:</strong> Redding, CA & Southern Oregon<br/>
    <strong>Details:</strong> Labor Day Coast Road Trip<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Aug 8, 2019 – Aug 12, 2019</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Lihue, Kapaʻa & Koloa, Kauai, HI<br/>
    <strong>Details:</strong> Flight (United Airlines) & Island Exploration<br/>
    <strong>Companions:</strong> Onam Bharti, Rohit Das, Meera Devi, Tarun Kumar, Aparna
  </div>

  <div class="trip-card" data-category="international">
    <strong>Apr 4, 2019 – Apr 15, 2019</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Barcelona, Seville, Granada (Spain) & Lisbon (Portugal)<br/>
    <strong>Details:</strong> Iberian Peninsula Tour<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Feb 23, 2019 – Mar 3, 2019</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> New Delhi & Kolkata, India<br/>
    <strong>Details:</strong> Family Visit & City Trip<br/>
    <strong>Companions:</strong> Anusha, Meera, S N Das, Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Feb 14, 2019 – Feb 19, 2019</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Maui (Lahaina, Hana, Kaanapali), HI<br/>
    <strong>Details:</strong> Flight & Hotel Package (The Westin Maui)<br/>
    <strong>Companions:</strong> Onam Bharti, Rohit Das, Varun Khandelwal, Sumedha
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Dec 30, 2018 – Jan 7, 2019</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Grand Canyon Village, AZ & Northern CA<br/>
    <strong>Details:</strong> Road Trip & Enterprise Car Rental<br/>
    <strong>Companions:</strong> Rohit Das & Deep Prakash Gupta
  </div>

  <div class="trip-card" data-category="regional">
    <strong>Sep 15, 2018 – Sep 16, 2018</strong> <span class="trip-badge badge-regional">🚗 Regional</span><br/>
    <strong>Destination:</strong> Burney & McArthur-Burney Falls, CA<br/>
    <strong>Details:</strong> Northern California Falls Getaway<br/>
    <strong>Companions:</strong> Rohit Das, Onam Bharti + Friends
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Aug 30, 2018 – Sep 3, 2018</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Las Vegas (NV), Grand Canyon North Rim (AZ) & Valley of Fire (UT/NV)<br/>
    <strong>Details:</strong> Desert Southwest National Parks Expedition<br/>
    <strong>Companions:</strong> Rohit Das & Onam Bharti
  </div>

  <div class="trip-card" data-category="international">
    <strong>May 24, 2018 – Jun 3, 2018</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Paris (France) | Bern, Grindelwald, Lauterbrunnen, Lucerne (Switzerland)<br/>
    <strong>Details:</strong> French Capital & Swiss Alps Train Tour<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="regional">
    <strong>Mar 31, 2018 – Apr 1, 2018</strong> <span class="trip-badge badge-regional">🚗 Regional</span><br/>
    <strong>Destination:</strong> Truckee & Tahoe National Forest, CA<br/>
    <strong>Details:</strong> Lake Tahoe Spring Weekend<br/>
    <strong>Companions:</strong> Onam Bharti
  </div>

  <div class="trip-card" data-category="international">
    <strong>Feb 17, 2018 – Feb 24, 2018</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> New York / Jersey City & Delhi, India<br/>
    <strong>Details:</strong> Flight (Jet Airways via Concur)<br/>
    <strong>Companions:</strong> Rohit Das & Onam Bharti
  </div>

  <div class="trip-card" data-category="international">
    <strong>Dec 10, 2017 – Jan 1, 2018</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Bangalore, Delhi, Kolkata & Gurugram, India<br/>
    <strong>Details:</strong> Flight (KLM, Turkish Airlines, Air India)<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Oct 1, 2017</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Budapest, Hungary<br/>
    <strong>Details:</strong> European City Photo Visit<br/>
    <strong>Companions:</strong> Solo
  </div>

  <div class="trip-card" data-category="international">
    <strong>Sep 22, 2017 – Sep 24, 2017</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Taoyuan (Taiwan) & Bali (Indonesia)<br/>
    <strong>Details:</strong> Asia Transit & Island Getaway<br/>
    <strong>Companions:</strong> Solo
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Jul 1, 2017 – Jul 2, 2017</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> White Sands National Park & Lordsburg, NM<br/>
    <strong>Details:</strong> New Mexico National Park Trip<br/>
    <strong>Companions:</strong> Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>May 13, 2017 – May 29, 2017</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Kolkata & Delhi (India) | Alturas, CA<br/>
    <strong>Details:</strong> International Family Visit & Northern CA Drive<br/>
    <strong>Companions:</strong> Rohit Das, Shambhu Nath Das, S N Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Feb 10, 2017 – Feb 12, 2017</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Arizona & Las Vegas, NV<br/>
    <strong>Details:</strong> Weekend Desert Drive<br/>
    <strong>Companions:</strong> Solo
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Jan 30, 2017 – Jan 31, 2017</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Carlsbad & San Diego, CA<br/>
    <strong>Details:</strong> Flight & Hotel (Southwest Airlines)<br/>
    <strong>Companions:</strong> Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Sep 1, 2016 – Sep 11, 2016</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Venice, Florence, Cinque Terre, Rome (Italy) & Vatican City<br/>
    <strong>Details:</strong> Italian Rail & Cultural Expedition<br/>
    <strong>Companions:</strong> Rohit Das & Onam Bharti
  </div>

  <div class="trip-card" data-category="international">
    <strong>Jul 2, 2016 – Jul 3, 2016</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Vancouver & Whistler, British Columbia, Canada<br/>
    <strong>Details:</strong> Pacific Northwest Getaway<br/>
    <strong>Companions:</strong> Onam Bharti
  </div>

  <div class="trip-card" data-category="international">
    <strong>Dec 11, 2015 – Jan 10, 2016</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Bangkok & Krabi (Thailand) | Delhi & Mandarmani (India)<br/>
    <strong>Details:</strong> Southeast Asia & India Winter Vacation<br/>
    <strong>Companions:</strong> Onam Bharti, Rohit Das, Nithin Das, S N Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Sep 5, 2015 – Sep 8, 2015</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Salt Lake City (UT) & Yellowstone / Grand Teton NP (WY)<br/>
    <strong>Details:</strong> Rocky Mountain National Parks Trip<br/>
    <strong>Companions:</strong> Meera, Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="regional">
    <strong>Jul 3, 2015 – Jul 5, 2015</strong> <span class="trip-badge badge-regional">🚗 Regional</span><br/>
    <strong>Destination:</strong> Anaheim & Southern California<br/>
    <strong>Details:</strong> Hotel Stay & Disneyland Region<br/>
    <strong>Companions:</strong> Rohit Das, Siddhartha Datta, Sutapa Dey
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>May 2, 2015 – May 10, 2015</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Chicago, IL & Seattle, WA<br/>
    <strong>Details:</strong> Flight (United Airlines)<br/>
    <strong>Companions:</strong> Rohit Das & Onam Bharti
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Sep 26, 2014 – Oct 5, 2014</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Raleigh/Durham, NC<br/>
    <strong>Details:</strong> Flight (US Airways)<br/>
    <strong>Companions:</strong> Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Feb 8, 2014 – Feb 17, 2014</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Cancun, Mexico & Miami, FL<br/>
    <strong>Details:</strong> Flight & Hotel Package (InterContinental Cancun)<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Sep 12, 2013 – Oct 5, 2013</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Dubai (UAE) & Kolkata / Delhi (India)<br/>
    <strong>Details:</strong> Flight (Emirates Air & IndiGo)<br/>
    <strong>Companions:</strong> Rohit Das & Onam Bharti
  </div>

  <div class="trip-card" data-category="regional">
    <strong>Aug 10, 2013 – Aug 11, 2013</strong> <span class="trip-badge badge-regional">🚗 Regional</span><br/>
    <strong>Destination:</strong> South Lake Tahoe, CA<br/>
    <strong>Details:</strong> Mountain Lake Escape<br/>
    <strong>Companions:</strong> Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>May 24, 2013 – May 28, 2013</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> San Diego, CA<br/>
    <strong>Details:</strong> Flight (United Airlines)<br/>
    <strong>Companions:</strong> Rohit Das & Onam Bharti
  </div>

  <div class="trip-card" data-category="international">
    <strong>Mar 10, 2013 – Apr 2, 2013</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Istanbul & Cappadocia (Türkiye) & Delhi (India)<br/>
    <strong>Details:</strong> Flight (Turkish Airlines) & Cave Hotel Stay<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Oct 26, 2012 – Nov 27, 2012</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Chennai, Kolkata, Patna & Delhi, India<br/>
    <strong>Details:</strong> Flight (Cathay Pacific & Jet Lite)<br/>
    <strong>Companions:</strong> Onam Bharti & Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Oct 3, 2012 – Oct 6, 2012</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Phoenix, AZ & Las Vegas, NV<br/>
    <strong>Details:</strong> Southwest Drive & Flight<br/>
    <strong>Companions:</strong> Rohit Das & Onam Bharti
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Dec 24, 2011 – Jan 2, 2012</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> New York, NY & NW Arkansas<br/>
    <strong>Details:</strong> Flight (American Airlines)<br/>
    <strong>Companions:</strong> Rohit Das & Shambhu Nath Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Nov 17, 2011 – Jan 15, 2012</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Kolkata, India to San Francisco, CA<br/>
    <strong>Details:</strong> Flight (Lufthansa & United Airlines)<br/>
    <strong>Companions:</strong> Shambhu Nath Das & Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Mar 7, 2011</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Chennai, India<br/>
    <strong>Details:</strong> Flight (JetKonnect)<br/>
    <strong>Companions:</strong> Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Nov 25, 2010 – Dec 20, 2010</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Kolkata, India (via Hong Kong & Bangkok)<br/>
    <strong>Details:</strong> Flight (Cathay Pacific)<br/>
    <strong>Companions:</strong> Rohit Das
  </div>

  <div class="trip-card" data-category="international">
    <strong>Nov 24, 2009</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Patna & Chennai, India<br/>
    <strong>Details:</strong> Train (IRCTC Sanghamitra Express)<br/>
    <strong>Companions:</strong> Onam Bharti
  </div>

  <div class="trip-card" data-category="international">
    <strong>Feb 13, 2009 – Mar 15, 2009</strong> <span class="trip-badge badge-international">🌍 International</span><br/>
    <strong>Destination:</strong> Kolkata & Chennai, India<br/>
    <strong>Details:</strong> Flight (British Airways & American Airlines)<br/>
    <strong>Companions:</strong> Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>Aug 17, 2007</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Phoenix, AZ (from Seattle)<br/>
    <strong>Details:</strong> Flight (Alaska Airlines)<br/>
    <strong>Companions:</strong> Rohit Das
  </div>

  <div class="trip-card" data-category="domestic">
    <strong>May 14, 2007 – May 15, 2007</strong> <span class="trip-badge badge-domestic">✈️ Domestic</span><br/>
    <strong>Destination:</strong> Federal Way & Seattle, WA<br/>
    <strong>Details:</strong> Flight & Hotel (Alaska Airlines)<br/>
    <strong>Companions:</strong> Rohit Das
  </div>

</div>

<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script src="https://unpkg.com/leaflet.markercluster@1.5.3/dist/leaflet.markercluster.js"></script>

<script>
  // 1. Initialize Map
  const map = L.map('travel-map').setView([20, 0], 2);

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 18,
    attribution: '© OpenStreetMap contributors'
  }).addTo(map);

  const markers = L.markerClusterGroup();

  // Custom Color SVG Pins
  function createCustomIcon(color) {
    const svg = `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="28" height="28"><path fill="${color}" stroke="#ffffff" stroke-width="1.5" d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/></svg>`;
    return L.divIcon({
      html: svg,
      className: '',
      iconSize: [28, 28],
      iconAnchor: [14, 28],
      popupAnchor: [0, -28]
    });
  }

  const redIcon = createCustomIcon('#d9534f');   // International
  const blueIcon = createCustomIcon('#0275d8');  // Domestic
  const greenIcon = createCustomIcon('#5cb85c'); // Regional

  // Destination Markers Data
  const locations = [
    // International (Red)
    { lat: 35.6762, lng: 139.6503, title: "Tokyo, Japan", type: "international", date: "Nov 2026" },
    { lat: 37.5665, lng: 126.9780, title: "Seoul, South Korea", type: "international", date: "Nov 2026" },
    { lat: 25.8130, lng: -77.9400, title: "CocoCay, The Bahamas", type: "international", date: "Jun 2026" },
    { lat: -0.9023, lng: -89.6100, title: "Galápagos Islands, Ecuador", type: "international", date: "Dec 2025" },
    { lat: -0.1807, lng: -78.4678, title: "Quito, Ecuador", type: "international", date: "Dec 2025" },
    { lat: 60.3913, lng: 5.3221, title: "Bergen, Norway", type: "international", date: "Aug 2025" },
    { lat: 59.9139, lng: 10.7522, title: "Oslo, Norway", type: "international", date: "Aug 2025" },
    { lat: 62.4722, lng: 6.1495, title: "Ålesund, Norway", type: "international", date: "Aug 2025" },
    { lat: 7.8804, lng: 98.3923, title: "Phuket & Ao Nang, Thailand", type: "international", date: "Mar 2025" },
    { lat: 22.8905, lng: -109.9167, title: "Cabo San Lucas, Mexico", type: "international", date: "Dec 2024" },
    { lat: 41.3851, lng: 2.1734, title: "Barcelona, Spain", type: "international", date: "Apr 2019 / Oct 2024" },
    { lat: 64.1466, lng: -21.9426, title: "Reykjavik & Ring Road, Iceland", type: "international", date: "Aug 2024" },
    { lat: 48.1351, lng: 11.5820, title: "Munich, Germany", type: "international", date: "Mar 2024" },
    { lat: 47.8095, lng: 13.0550, title: "Salzburg & Hallstatt, Austria", type: "international", date: "Apr 2024" },
    { lat: 42.6507, lng: 18.0944, title: "Dubrovnik & Split, Croatia", type: "international", date: "Apr 2024" },
    { lat: 30.0444, lng: 31.2357, title: "Cairo, Giza & Luxor, Egypt", type: "international", date: "Nov 2023" },
    { lat: 55.9533, lng: -3.1883, title: "Edinburgh, Scotland", type: "international", date: "Jul 2023" },
    { lat: 51.5074, lng: -0.1278, title: "London & Cotswolds, UK", type: "international", date: "Jul 2023" },
    { lat: 41.0082, lng: 28.9784, title: "Istanbul & Cappadocia, Türkiye", type: "international", date: "Mar 2013 / Mar 2023" },
    { lat: -13.1631, lng: -72.5450, title: "Machu Picchu & Cusco, Peru", type: "international", date: "Nov 2022" },
    { lat: 37.9838, lng: 23.7275, title: "Athens & Santorini, Greece", type: "international", date: "Apr 2022" },
    { lat: 52.3676, lng: 4.9041, title: "Amsterdam, Netherlands", type: "international", date: "Apr 2022" },
    { lat: 20.6534, lng: -105.2253, title: "Puerto Vallarta, Mexico", type: "international", date: "Nov 2021" },
    { lat: 51.1784, lng: -115.5708, title: "Banff & Jasper NP, Canada", type: "international", date: "Aug 2021" },
    { lat: 21.1619, lng: -86.8515, title: "Cancun, Mexico", type: "international", date: "Feb 2014 / Feb 2020" },
    { lat: 38.7223, lng: -9.1393, title: "Lisbon, Portugal", type: "international", date: "Apr 2019" },
    { lat: 28.6139, lng: 77.2090, title: "Delhi, India", type: "international", date: "Multiple Visits" },
    { lat: 22.5726, lng: 88.3639, title: "Kolkata, India", type: "international", date: "Multiple Visits" },
    { lat: 48.8566, lng: 2.3522, title: "Paris, France", type: "international", date: "May 2018" },
    { lat: 46.9480, lng: 7.4474, title: "Bern & Grindelwald, Switzerland", type: "international", date: "May 2018" },
    { lat: -8.4095, lng: 115.1889, title: "Bali, Indonesia", type: "international", date: "Sep 2017" },
    { lat: 47.4979, lng: 19.0402, title: "Budapest, Hungary", type: "international", date: "Oct 2017" },
    { lat: 45.4371, lng: 12.3326, title: "Venice, Florence & Rome, Italy", type: "international", date: "Sep 2016" },
    { lat: 50.1163, lng: -122.9574, title: "Whistler & Vancouver, Canada", type: "international", date: "Jul 2016" },

    // Domestic US (Blue)
    { lat: 42.8864, lng: -78.8784, title: "Niagara Falls & Buffalo, NY", type: "domestic", date: "Jun 2026" },
    { lat: 25.7617, lng: -80.1918, title: "Miami Beach, FL", type: "domestic", date: "Jun 2026" },
    { lat: 47.6062, lng: -122.3321, title: "Seattle & Bellevue, WA", type: "domestic", date: "Multiple Visits" },
    { lat: 39.6533, lng: -105.2058, title: "Red Rocks Amphitheatre, CO", type: "domestic", date: "May 2025" },
    { lat: 35.8082, lng: -83.5771, title: "Great Smoky Mountains NP, TN", type: "domestic", date: "Apr 2024" },
    { lat: 21.3069, lng: -157.8583, title: "Honolulu, Oahu, HI", type: "domestic", date: "Dec 2023" },
    { lat: 64.8378, lng: -147.7164, title: "Fairbanks & Anchorage, AK", type: "domestic", date: "Feb 2023" },
    { lat: 37.2982, lng: -113.0263, title: "Zion National Park, UT", type: "domestic", date: "Jul 2022" },
    { lat: 36.1699, lng: -115.1398, title: "Las Vegas, NV", type: "domestic", date: "Multiple Visits" },
    { lat: 19.5429, lng: -155.6659, title: "Big Island, HI", type: "domestic", date: "Mar 2021" },
    { lat: 22.0964, lng: -159.5261, title: "Kauai, HI", type: "domestic", date: "Aug 2019" },
    { lat: 20.7984, lng: -156.3319, title: "Maui, HI", type: "domestic", date: "Feb 2019" },
    { lat: 36.0544, lng: -112.1401, title: "Grand Canyon National Park, AZ", type: "domestic", date: "Aug 2018 / Jan 2019" },
    { lat: 32.7797, lng: -106.1717, title: "White Sands NP, NM", type: "domestic", date: "Jul 2017" },
    { lat: 44.4280, lng: -110.5885, title: "Yellowstone National Park, WY", type: "domestic", date: "Sep 2015" },
    { lat: 41.8781, lng: -87.6298, title: "Chicago, IL", type: "domestic", date: "May 2015" },

    // Regional Getaways (Green)
    { lat: 37.9577, lng: -118.9721, title: "Mammoth Lakes & June Lake, CA", type: "regional", date: "Jul 2025" },
    { lat: 37.8177, lng: -120.6624, title: "Knights Ferry, CA", type: "regional", date: "Apr 2025" },
    { lat: 39.4285, lng: -123.8018, title: "Fort Bragg & Redwoods, CA", type: "regional", date: "May 2023" },
    { lat: 38.2505, lng: -120.3088, title: "Dorrington, Sierra Nevada, CA", type: "regional", date: "Dec 2022" },
    { lat: 37.8651, lng: -119.5383, title: "Yosemite National Park, CA", type: "regional", date: "Feb 2022" },
    { lat: 34.6141, lng: -120.0884, title: "Santa Ynez Wine Country, CA", type: "regional", date: "Oct 2021" },
    { lat: 44.1507, lng: -122.6073, title: "McKenzie River & Eugene, OR", type: "regional", date: "Sep 2020" },
    { lat: 41.0104, lng: -121.6528, title: "Burney Falls, CA", type: "regional", date: "Sep 2018" },
    { lat: 39.3280, lng: -120.1833, title: "Truckee & Lake Tahoe, CA", type: "regional", date: "Aug 2013 / Mar 2018" }
  ];

  locations.forEach(loc => {
    let icon = blueIcon;
    if (loc.type === 'international') icon = redIcon;
    if (loc.type === 'regional') icon = greenIcon;

    const marker = L.marker([loc.lat, loc.lng], { icon: icon })
      .bindPopup(`<strong>${loc.title}</strong><br/>Category: ${loc.type.toUpperCase()}<br/>Visited: ${loc.date}`);
    markers.addLayer(marker);
  });

  map.addLayer(markers);

  // 2. JS Filter Buttons Functionality
  function filterTrips(category) {
    const cards = document.querySelectorAll('.trip-card');
    const buttons = document.querySelectorAll('.filter-btn');

    buttons.forEach(btn => btn.classList.remove('active'));
    event.target.classList.add('active');

    cards.forEach(card => {
      if (category === 'all' || card.getAttribute('data-category') === category) {
        card.style.display = 'block';
      } else {
        card.style.display = 'none';
      }
    });
  }
</script>
