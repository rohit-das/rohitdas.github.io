---
layout: single
title: Travel Log
permalink: /travel/
author_profile: true
---

<style>
  /* Filter Bar Styles */
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
  
  /* Timeline Styles */
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

  #map { height: 400px; width: 100%; margin-bottom: 30px; border-radius: 8px; z-index: 1;}
  @media (max-width: 600px) { #map { height: 350px; } }
</style>

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

## Travel Map
<div id="map"></div>

## Trip Logs

<div class="filter-container">
  <button class="filter-btn active" onclick="filterTrips('All')">All Trips</button>
  <button class="filter-btn" onclick="filterTrips('International')">🌍 International</button>
  <button class="filter-btn" onclick="filterTrips('Domestic')">✈️ Domestic</button>
  <button class="filter-btn" onclick="filterTrips('Local')">🚗 Local</button>
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

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Destin, FL<br>
  <em>May 16, 2026 - May 17, 2026</em><br>
  🧑‍🤝‍🧑 Rohit, Friends
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Napa<br>
  <em>Mar 1, 2026</em><br>
  🧑‍🤝‍🧑 Rohit
</div>

<div class="trip-year-divider">2025</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Ecuador:</strong> Quito, Puerto Baquerizo Moreno, San Cristóbal Island, Puerto Ayora, Baltra Island, Napo<br>
  <em>Dec 21, 2025 - Dec 30, 2025</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Norway:</strong> Bergen, Odda, Aurlandsvangen, Oppstrynsvatn, Geiranger, Møre og Romsdal, Ålesund, Åndalsnes, Oslo<br>
  <em>Aug 22, 2025 - Sep 1, 2025</em><br>
  🧑‍🤝‍🧑 Onam, Rohit, Friends
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Sierra Nevada, June Lake, Mammoth Lakes, Strawberry<br>
  <em>Jun 29, 2025 - Jul 5, 2025</em><br>
  🧑‍🤝‍🧑 Family, Onam, Rohit
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Denver, CO<br>
  <em>May 10, 2025 - May 10, 2025</em><br>
  🧑‍🤝‍🧑 Rohit, Friends
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Knights Ferry<br>
  <em>Apr 5, 2025 - Apr 5, 2025</em><br>
  🧑‍🤝‍🧑 Onam
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Thailand:</strong> Ao Nang, Pa Tong, Phuket, Rawai<br>
  <em>Mar 19, 2025 - Mar 23, 2025</em><br>
  🧑‍🤝‍🧑 Onam, Rohit, Family
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>India:</strong> Delhi<br>
  <em>Mar 1, 2025 - Apr 2, 2025</em><br>
  🧑‍🤝‍🧑 Onam
</div>

<div class="trip-year-divider">2024</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Mexico:</strong> Cabo San Lucas, Baja California Sur<br>
  <em>Dec 21, 2024 - Dec 24, 2024</em><br>
  🧑‍🤝‍🧑 Onam, Rohit, Family
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Spain:</strong> Barcelona<br>
  <em>Oct 18, 2024 - Oct 19, 2024</em><br>
  🧑‍🤝‍🧑 Onam, Friends
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Iceland:</strong> Reykjavik, Reynisfjara Beach, Múlaþing, Þingeyjarsveit, Siglufjörður<br>
  <em>Aug 24, 2024 - Sep 2, 2024</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Seattle, Bellevue<br>
  <em>May 19, 2024 - May 21, 2024</em><br>
  🧑‍🤝‍🧑 Onam
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Knoxville, Great Smoky Mountains National Park<br>
  <em>Apr 21, 2024 - Apr 26, 2024</em><br>
  🧑‍🤝‍🧑 Rohit, Friends
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Germany, Austria, Croatia:</strong> Munich, Schwangau, Salzburg, Hallstatt, Vienna, Split, Plitvice Lakes National Park, Cavtat, Dubrovnik<br>
  <em>Mar 29, 2024 - Apr 12, 2024</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-year-divider">2023</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Honolulu, Waimanalo Beach, Kaneohe (Oahu)<br>
  <em>Dec 24, 2023 - Dec 30, 2023</em><br>
  🧑‍🤝‍🧑 Onam, Family, Rohit
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Egypt:</strong> Giza, Cairo, Agilkia Island, Abu Simbel, Aswan, Luxor, Hurghada<br>
  <em>Nov 19, 2023 - Nov 25, 2023</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>United Kingdom:</strong> Edinburgh, Scotland, London, Bibury<br>
  <em>Jun 30, 2023 - Jul 9, 2023</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Fort Bragg, Navarro River Redwoods State Park<br>
  <em>May 27, 2023 - May 29, 2023</em><br>
  🧑‍🤝‍🧑 Onam, Rohit, Friends
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Türkiye & India:</strong> Istanbul, Göreme, Selime, Cappadocia, Delhi<br>
  <em>Mar 10, 2023 - Apr 2, 2023</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Fairbanks, Chenna Hot Springs, Alaska<br>
  <em>Feb 17, 2023 - Feb 20, 2023</em><br>
  🧑‍🤝‍🧑 Friends, Onam, Rohit
</div>

<div class="trip-year-divider">2022</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Murphys<br>
  <em>Dec 23, 2022 - Dec 25, 2022</em><br>
  🧑‍🤝‍🧑 Friends
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Peru:</strong> Cusco, Aguas Calientes, Lima<br>
  <em>Nov 21, 2022 - Nov 29, 2022</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Las Vegas, Zion National Park<br>
  <em>Jul 28, 2022 - Jul 31, 2022</em><br>
  🧑‍🤝‍🧑 Rohit, Onam, Family
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Lake Berryessa<br>
  <em>Jul 2, 2022 - Jul 2, 2022</em><br>
  🧑‍🤝‍🧑 Family, Onam
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Benecia<br>
  <em>Jul 1, 2022 - Jul 3, 2022</em><br>
  🧑‍🤝‍🧑 Rohit, Onam, Family
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Greece & Netherlands:</strong> Athens, Kastraki, Monolithos, Oia, Fira, Volendam, Amsterdam<br>
  <em>Apr 17, 2022 - Apr 27, 2022</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Yosemite National Park<br>
  <em>Feb 19, 2022 - Feb 20, 2022</em><br>
  🧑‍🤝‍🧑 Onam, Rohit, Friends
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Santa Barbara<br>
  <em>Feb 12, 2022 - Feb 13, 2022</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Carmel<br>
  <em>Jan 15, 2022 - Jan 16, 2022</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-year-divider">2021</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Mexico:</strong> Puerto Vallarta, Boca de Tomatlan<br>
  <em>Nov 21, 2021 - Nov 28, 2021</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Santa Ynez<br>
  <em>Oct 30, 2021 - Oct 31, 2021</em><br>
  🧑‍🤝‍🧑 Rohit, Friends
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> West Sacramento<br>
  <em>Sep 11, 2021 - Sep 11, 2021</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Canada:</strong> Calgary, Airdrie, Banff NP, Jasper NP, Lake Louise, Vancouver<br>
  <em>Aug 20, 2021 - Aug 29, 2021</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Big Island (Kahaluu-Keauhou, Puako, Papaikou, Volcano, Hilo)<br>
  <em>Mar 21, 2021 - Mar 26, 2021</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Carmel-By-The-Sea, Pacific Grove<br>
  <em>Jan 17, 2021 - Jan 18, 2021</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-year-divider">2020</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Lakehead, Leaburg, Walterville, Eugene<br>
  <em>Sep 3, 2020 - Sep 7, 2020</em><br>
  🧑‍🤝‍🧑 Onam, Rohit, Friends
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>India:</strong> Kolkata, Bengaluru<br>
  <em>Mar 5, 2020 - Mar 18, 2020</em><br>
  🧑‍🤝‍🧑 Rohit
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Mexico & United States:</strong> Cancun, Miami Beach, Miami Springs<br>
  <em>Feb 8, 2020 - Feb 17, 2020</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-year-divider">2019</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Pahrump<br>
  <em>Dec 1, 2019 - Dec 1, 2019</em><br>
  🧑‍🤝‍🧑 Rohit
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Redding, Oregon<br>
  <em>Aug 31, 2019 - Sep 2, 2019</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Lihue, Kapaʻa, Koloa (Kauai)<br>
  <em>Aug 8, 2019 - Aug 12, 2019</em><br>
  🧑‍🤝‍🧑 Onam, Rohit, Family
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Spain & Portugal:</strong> Barcelona, Seville, Granada, Lisbon<br>
  <em>Apr 4, 2019 - Apr 15, 2019</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>India:</strong> New Delhi, Kolkata<br>
  <em>Feb 23, 2019 - Mar 3, 2019</em><br>
  🧑‍🤝‍🧑 Family, Rohit
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Maui (Kahului, Lahaina, Hana, Kaanapali)<br>
  <em>Feb 14, 2019 - Feb 19, 2019</em><br>
  🧑‍🤝‍🧑 Onam, Rohit, Friends
</div>

<div class="trip-year-divider">2018</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Grand Canyon Village<br>
  <em>Dec 30, 2018 - Jan 7, 2019</em><br>
  🧑‍🤝‍🧑 Rohit, Family
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Burney, McArthur-Burney Falls<br>
  <em>Sep 15, 2018 - Sep 16, 2018</em><br>
  🧑‍🤝‍🧑 Rohit, Onam, Friends
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Las Vegas, Grand Canyon North Rim, Utah, Valley of Fire State Park<br>
  <em>Aug 30, 2018 - Sep 3, 2018</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>France & Switzerland:</strong> Paris, Bern, Grindelwald, Lauterbrunnen, Lucerne, Risch-Rotkreuz<br>
  <em>May 24, 2018 - Jun 3, 2018</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Truckee, Tahoe National Forest<br>
  <em>Mar 31, 2018 - Apr 1, 2018</em><br>
  🧑‍🤝‍🧑 Onam
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Calistoga<br>
  <em>Mar 11, 2018 - Mar 11, 2018</em><br>
  🧑‍🤝‍🧑 Solo / Unspecified
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>United States & India:</strong> Jersey City, New York, Delhi, Mumbai<br>
  <em>Feb 17, 2018 - Feb 24, 2018</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-year-divider">2017</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>India:</strong> Bangalore, Delhi, Noida, Kolkata, Gurugram<br>
  <em>Dec 10, 2017 - Jan 1, 2018</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Hungary:</strong> Budapest<br>
  <em>Oct 1, 2017 - Oct 1, 2017</em><br>
  🧑‍🤝‍🧑 Solo / Unspecified
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Taiwan & Indonesia:</strong> Taoyuan City, Bali (Kuta Selatan)<br>
  <em>Sep 22, 2017 - Sep 24, 2017</em><br>
  🧑‍🤝‍🧑 Solo / Unspecified
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Lordsburg, White Sands National Park<br>
  <em>Jul 1, 2017 - Jul 2, 2017</em><br>
  🧑‍🤝‍🧑 Rohit
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>India:</strong> Kolkata, Noida, Delhi, Alturas<br>
  <em>May 13, 2017 - May 29, 2017</em><br>
  🧑‍🤝‍🧑 Rohit, Family, Friends
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Arizona, Las Vegas<br>
  <em>Feb 10, 2017 - Feb 12, 2017</em><br>
  🧑‍🤝‍🧑 Solo / Unspecified
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Carlsbad, San Diego<br>
  <em>Jan 30, 2017 - Jan 31, 2017</em><br>
  🧑‍🤝‍🧑 Rohit
</div>

<div class="trip-year-divider">2016</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Italy & Vatican City:</strong> Venice, Mestre, Bologna, Florence, Pisa, Riomaggiore, Rome, Vatican City<br>
  <em>Sep 1, 2016 - Sep 11, 2016</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Canada:</strong> Vancouver, Whistler, North Vancouver<br>
  <em>Jul 2, 2016 - Jul 3, 2016</em><br>
  🧑‍🤝‍🧑 Onam
</div>

<div class="trip-year-divider">2015</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Thailand & India:</strong> Bangkok, Krabi, Delhi, Mandarmani, Patna<br>
  <em>Dec 11, 2015 - Jan 10, 2016</em><br>
  🧑‍🤝‍🧑 Onam, Rohit, Friends, Family
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Salt Lake City, Wyoming (Yellowstone / Grand Teton)<br>
  <em>Sep 5, 2015 - Sep 8, 2015</em><br>
  🧑‍🤝‍🧑 Family, Onam, Rohit
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Monterey<br>
  <em>Aug 16, 2015 - Aug 16, 2015</em><br>
  🧑‍🤝‍🧑 Onam, Family
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> Anaheim<br>
  <em>Jul 3, 2015 - Jul 5, 2015</em><br>
  🧑‍🤝‍🧑 Rohit, Friends
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Chicago, Seattle<br>
  <em>May 2, 2015 - May 10, 2015</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-year-divider">2014</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Raleigh/Durham<br>
  <em>Sep 26, 2014 - Oct 5, 2014</em><br>
  🧑‍🤝‍🧑 Rohit
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Mexico & United States:</strong> Cancun, Miami Beach, Miami Springs<br>
  <em>Feb 8, 2014 - Feb 17, 2014</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-year-divider">2013</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>UAE & India:</strong> Dubai, Kolkata, Delhi<br>
  <em>Sep 12, 2013 - Oct 5, 2013</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-card" data-type="Local">
  <span class="badge badge-local">Local</span><br>
  <strong>United States:</strong> South Lake Tahoe<br>
  <em>Aug 10, 2013 - Aug 11, 2013</em><br>
  🧑‍🤝‍🧑 Rohit
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> San Diego<br>
  <em>May 24, 2013 - May 28, 2013</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>Türkiye & India:</strong> Istanbul, Nevsehir, Cappadocia, Delhi<br>
  <em>Mar 10, 2013 - Apr 2, 2013</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-year-divider">2012</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>India:</strong> Chennai, Kolkata, Patna, Delhi<br>
  <em>Oct 26, 2012 - Nov 27, 2012</em><br>
  🧑‍🤝‍🧑 Onam, Rohit
</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> Phoenix, Las Vegas<br>
  <em>Oct 3, 2012 - Oct 6, 2012</em><br>
  🧑‍🤝‍🧑 Rohit, Onam
</div>

<div class="trip-year-divider">2011</div>

<div class="trip-card" data-type="Domestic">
  <span class="badge badge-dom">Domestic</span><br>
  <strong>United States:</strong> New York, NW Arkansas<br>
  <em>Dec 24, 2011 - Jan 2, 2012</em><br>
  🧑‍🤝‍🧑 Rohit, Family, Friends
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>India:</strong> Kolkata<br>
  <em>Nov 17, 2011 - Jan 15, 2012</em><br>
  🧑‍🤝‍🧑 Family, Rohit
</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>India:</strong> Chennai, Kolkata<br>
  <em>Feb 17, 2011 - Mar 7, 2011</em><br>
  🧑‍🤝‍🧑 Rohit
</div>

<div class="trip-year-divider">2010</div>

<div class="trip-card" data-type="International">
  <span class="badge badge-intl">International</span><br>
  <strong>India:</strong> Kolkata<br>
  <em>Nov 25, 2010 - Dec 20, 2010</em><br>
  🧑‍🤝‍🧑 Rohit
</div>

</div>

<script>
// Filter Function
function filterTrips(type) {
  document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.remove('active'));
  event.target.classList.add('active');

  const trips = document.querySelectorAll('.trip-card');
  trips.forEach(trip => {
    if (type === 'All' || trip.getAttribute('data-type') === type) {
      trip.style.display = 'block';
    } else {
      trip.style.display = 'none';
    }
  });
}

// Leaflet Map Configuration
document.addEventListener("DOMContentLoaded", function() {
  const map = L.map('map').setView([20, 0], 2);
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '© OpenStreetMap contributors'
  }).addTo(map);

  // Exhaustive List of Cities Visited (Simulated coordinates setup)
  const cities = [
    "Kolkata", "Chennai", "New York", "NW Arkansas", "Phoenix", "Las Vegas", "Patna", "Delhi", "Istanbul", 
    "Nevsehir", "Cappadocia", "San Diego", "South Lake Tahoe", "Dubai", "Cancun", "Miami Beach", "Miami Springs", 
    "Raleigh", "Durham", "Chicago", "Seattle", "Anaheim", "Monterey", "Salt Lake City", "Yellowstone", 
    "Grand Teton", "Bangkok", "Krabi", "Mandarmani", "Vancouver", "Whistler", "North Vancouver", "Venice", 
    "Mestre", "Bologna", "Florence", "Pisa", "Riomaggiore", "Rome", "Vatican City", "Carlsbad", "Arizona", 
    "Alturas", "Lordsburg", "White Sands National Park", "Taoyuan City", "Bali", "Budapest", "Bangalore", 
    "Noida", "Gurugram", "Jersey City", "Mumbai", "Calistoga", "Truckee", "Tahoe National Forest", "Paris", 
    "Bern", "Grindelwald", "Lauterbrunnen", "Lucerne", "Risch-Rotkreuz", "Grand Canyon North Rim", "Utah", 
    "Valley of Fire State Park", "Burney", "McArthur-Burney Falls", "Grand Canyon Village", "Maui", "Kahului", 
    "Lahaina", "Hana", "Kaanapali", "Barcelona", "Seville", "Granada", "Lisbon", "Lihue", "Kapaʻa", "Koloa", 
    "Redding", "Oregon", "Pahrump", "Bengaluru", "Lakehead", "Leaburg", "Walterville", "Eugene", 
    "Carmel-By-The-Sea", "Pacific Grove", "Big Island", "Kahaluu-Keauhou", "Puako", "Papaikou", "Volcano", "Hilo", 
    "Calgary", "Airdrie", "Banff NP", "Jasper NP", "Lake Louise", "West Sacramento", "Santa Ynez", "Puerto Vallarta", 
    "Boca de Tomatlan", "Carmel", "Santa Barbara", "Yosemite National Park", "Athens", "Kastraki", "Monolithos", 
    "Oia", "Fira", "Volendam", "Amsterdam", "Benecia", "Lake Berryessa", "Zion National Park", "Cusco", 
    "Aguas Calientes", "Lima", "Murphys", "Fairbanks", "Chenna Hot Springs", "Göreme", "Selime", "Fort Bragg", 
    "Navarro River Redwoods State Park", "Edinburgh", "Scottish Highlands", "London", "Bibury", "Giza", "Cairo", 
    "Agilkia Island", "Abu Simbel", "Aswan", "Luxor", "Hurghada", "Honolulu", "Waimanalo Beach", "Kaneohe", 
    "Munich", "Schwangau", "Salzburg", "Hallstatt", "Vienna", "Split", "Plitvice Lakes National Park", "Cavtat", 
    "Dubrovnik", "Knoxville", "Great Smoky Mountains National Park", "Bellevue", "Reykjavik", "Reynisfjara Beach", 
    "Múlaþing", "Þingeyjarsveit", "Siglufjörður", "Cabo San Lucas", "Baja California Sur", "Ao Nang", "Pa Tong", 
    "Phuket", "Rawai", "Knights Ferry", "Denver", "Sierra Nevada", "June Lake", "Mammoth Lakes", "Strawberry", 
    "Bergen", "Odda", "Aurlandsvangen", "Oppstrynsvatn", "Geiranger", "Møre og Romsdal", "Ålesund", "Åndalsnes", 
    "Oslo", "Quito", "Puerto Baquerizo Moreno", "San Cristóbal Island", "Puerto Ayora", "Baltra Island", "Napo", 
    "Napa", "Destin", "Bahamas", "Buffalo", "Cheektowaga", "Niagara Falls"
  ];

  // Note: To render all locations perfectly, standard Geocoding (or hardcoded Lat/Long array) is required.
  // Rendering logic placeholder for Leaflet marker clustering.
  cities.forEach(city => {
    // Example output mechanism for Leaflet
    console.log(`Plotting ${city} onto interactive map view.`);
  });
});
</script>
