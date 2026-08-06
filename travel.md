---
layout: single
title: "Travel Log"
permalink: /travel/
author_profile: true
---

<style>
  /* Base Container Styles */
  .travel-container {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    color: #222;
    margin-bottom: 2rem;
  }

  /* Stats Dashboard Grid - Mobile First */
  .stats-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-bottom: 20px;
  }
  .stat-card {
    background: #f8f9fa;
    border: 1px solid #e9ecef;
    border-radius: 8px;
    padding: 12px;
    text-align: center;
    flex: 1 1 calc(50% - 10px); /* 2 items per row on mobile */
    box-shadow: 0 1px 3px rgba(0,0,0,0.05);
  }
  .stat-card .number {
    font-size: 1.5rem;
    font-weight: 700;
    color: #2b6cb0;
    line-height: 1.2;
  }
  .stat-card .label {
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    color: #6c757d;
    margin-top: 4px;
  }

  /* Interactive Map Responsive Wrapper */
  #travel-map {
    width: 100%;
    height: 350px;
    border-radius: 8px;
    border: 1px solid #ddd;
    margin-bottom: 20px;
    z-index: 1;
  }

  /* Touch-Friendly Mobile Filter Buttons */
  .filter-bar {
    display: flex;
    gap: 8px;
    overflow-x: auto;
    padding-bottom: 8px;
    margin-bottom: 25px;
    -webkit-overflow-scrolling: touch;
  }
  .filter-btn {
    background: #edf2f7;
    border: 1px solid #cbd5e0;
    border-radius: 20px;
    padding: 6px 14px;
    font-size: 0.85rem;
    font-weight: 600;
    color: #4a5568;
    white-space: nowrap;
    cursor: pointer;
    transition: all 0.2s ease;
  }
  .filter-btn.active, .filter-btn:hover {
    background: #3182ce;
    color: #fff;
    border-color: #3182ce;
  }

  /* Timeline Log Styling */
  .year-section {
    border-top: 3px solid #333; /* Dark line between years */
    padding-top: 15px;
    margin-top: 25px;
  }
  .year-heading {
    font-size: 1.4rem;
    font-weight: 800;
    color: #1a202c;
    margin-bottom: 12px;
  }
  .trip-card {
    background: #fff;
    border-left: 4px solid #cbd5e0;
    border-radius: 0 6px 6px 0;
    padding: 12px 14px;
    margin-bottom: 12px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.06);
    transition: transform 0.15s ease;
  }
  .trip-card[data-type="International"] { border-left-color: #e53e3e; }
  .trip-card[data-type="Domestic"] { border-left-color: #3182ce; }
  .trip-card[data-type="Regional"] { border-left-color: #38a169; }

  .trip-header {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    flex-wrap: wrap;
    gap: 6px;
  }
  .trip-title {
    font-size: 1rem;
    font-weight: 700;
    color: #2d3748;
    margin: 0;
  }
  .badge {
    font-size: 0.7rem;
    padding: 2px 8px;
    border-radius: 12px;
    font-weight: 600;
    color: #fff;
    text-transform: uppercase;
  }
  .badge-international { background-color: #e53e3e; }
  .badge-domestic { background-color: #3182ce; }
  .badge-regional { background-color: #38a169; }

  .trip-meta {
    font-size: 0.8rem;
    color: #718096;
    margin-top: 4px;
  }
  .trip-details {
    font-size: 0.85rem;
    color: #4a5568;
    margin-top: 6px;
  }

  /* Desktop View Enhancements */
  @media (min-width: 768px) {
    #travel-map { height: 480px; }
    .stat-card { flex: 1 1 calc(25% - 12px); } /* 4 across on desktop */
    .stat-card .number { font-size: 1.8rem; }
  }
</style>

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<div class="travel-container">

  <div class="stats-grid">
    <div class="stat-card">
      <div class="number">47</div>
      <div class="label">Total Trips</div>
    </div>
    <div class="stat-card">
      <div class="number">20</div>
      <div class="label">Countries Visited</div>
    </div>
    <div class="stat-card">
      <div class="number">13</div>
      <div class="label">US States</div>
    </div>
    <div class="stat-card">
      <div class="number">2007</div>
      <div class="label">Logging Since</div>
    </div>
  </div>

  <div id="travel-map"></div>

  <div class="filter-bar">
    <button class="filter-btn active" onclick="filterTrips('all')">All Trips</button>
    <button class="filter-btn" onclick="filterTrips('International')">🌍 International</button>
    <button class="filter-btn" onclick="filterTrips('Domestic')">✈️ Domestic</button>
    <button class="filter-btn" onclick="filterTrips('Regional')">🚗 Regional</button>
  </div>

  <div class="year-section">
    <div class="year-heading">2026</div>
    
    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Bellevue & Seattle, WA</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Jun 8, 2026 – Jun 11, 2026 | 👥 Onam Bharti</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Miami Beach, Bahamas, Buffalo, Cheektowaga, Niagara Falls</span>
        <span class="badge badge-domestic">Domestic / Intl</span>
      </div>
      <div class="trip-meta">📅 Jun 14, 2026 – Jun 21, 2026 | 👥 Onam Bharti, Rohit Das, Anusha, Meera</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Destin, FL</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 May 16, 2026 – May 17, 2026 | 👥 Rohit Das and friends</div>
      <div class="trip-details">IIT Kgp US reunion trip</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2025</div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Quito, Galápagos Islands & Napo, Ecuador</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Dec 21, 2025 – Dec 30, 2025 | 👥 Onam Bharti, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Bergen, Odda, Geiranger, Ålesund, Åndalsnes, Oslo, Norway</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Aug 22, 2025 – Sep 1, 2025 | 👥 Onam Bharti, Rohit Das, Nithin and wife</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Sierra Nevada, June Lake, Mammoth Lakes, Strawberry, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 Jun 29, 2025 – Jul 5, 2025 | 👥 S N Das, Onam Bharti, Anusha, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Denver & Red Rocks Amphitheatre, CO</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 May 10, 2025 | 👥 Rohit Das and friends</div>
      <div class="trip-details">IIT Kgp US reunion trip</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Knights Ferry, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 Apr 5, 2025 | 👥 Onam Bharti</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Ao Nang, Pa Tong, Phuket, Rawai, Thailand</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Mar 19, 2025 – Mar 23, 2025 | 👥 Onam Bharti, Rohit Das and Family</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Delhi, India</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Mar 1, 2025 – Apr 2, 2025 | 👥 Onam Bharti</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2024</div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Cabo San Lucas, Baja California Sur, Mexico</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Dec 21, 2024 – Dec 24, 2024 | 👥 Onam Bharti, Rohit Das, Anusha</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Barcelona, Spain</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Oct 18, 2024 – Oct 19, 2024 | 👥 Onam Bharti and friends</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Reykjavik, Reynisfjara, Múlaþing, Þingeyjarsveit, Siglufjörður, Iceland</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Aug 24, 2024 – Sep 2, 2024 | 👥 Rohit Das, Onam Bharti</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Seattle & Bellevue, WA</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 May 19, 2024 – May 21, 2024 | 👥 Onam Bharti</div>
      <div class="trip-details">Work trip</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Knoxville & Great Smoky Mountains National Park, TN</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Apr 21, 2024 – Apr 26, 2024 | 👥 Rohit Das and friends</div>
      <div class="trip-details">IIT Kgp US reunion trip</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Munich, Salzburg, Vienna, Split, Plitvice Lakes, Dubrovnik</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Mar 29, 2024 – Apr 12, 2024 | 👥 Onam Bharti, Rohit Das</div>
      <div class="trip-details">Germany, Austria, Croatia</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2023</div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Honolulu, Waimanalo Beach, Kaneohe (Oahu), HI</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Dec 24, 2023 – Dec 30, 2023 | 👥 Onam Bharti, Anusha Gupta, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Giza, Cairo, Abu Simbel, Aswan, Luxor, Hurghada, Egypt</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Nov 19, 2023 – Nov 25, 2023 | 👥 Onam Bharti, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Edinburgh, London, Bibury, UK</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Jun 30, 2023 – Jul 9, 2023 | 👥 Rohit Das, Onam Bharti</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Fort Bragg & Navarro River Redwoods, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 May 27, 2023 – May 29, 2023 | 👥 Onam Bharti, Rohit Das, Dhruvil, Dhwani</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Istanbul, Göreme, Cappadocia, Delhi</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Mar 10, 2023 – Apr 2, 2023 | 👥 Onam Bharti, Rohit Das</div>
      <div class="trip-details">Türkiye & India</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Fairbanks, Castner Glacier & Chena Hot Springs, AK</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Feb 17, 2023 – Feb 20, 2023 | 👥 Dhwani, Dhruvil, Onam Bharti, Rohit Das, Varun, Sumi, JP, Aparna</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2022</div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Murphys, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 Dec 23, 2022 – Dec 25, 2022 | 👥 Aparna, JP, Neha Vatsyayan</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Cusco, Aguas Calientes, Machu Picchu, Lima, Peru</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Nov 21, 2022 – Nov 29, 2022 | 👥 Onam Bharti, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Las Vegas & Zion National Park, NV/UT</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Jul 28, 2022 – Jul 31, 2022 | 👥 Rohit Das, Onam Bharti, Meera Devi, Tarun Kumar</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Benicia, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 Jul 1, 2022 – Jul 3, 2022 | 👥 Rohit Das, Onam Bharti, Meera Devi, Tarun Kumar</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Delhi, India</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Jun 17, 2022 – Aug 27, 2022 | 👥 Meera Devi, Tarun Kumar</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Athens, Santorini, Volendam, Amsterdam</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Apr 17, 2022 – Apr 27, 2022 | 👥 Rohit Das, Onam Bharti</div>
      <div class="trip-details">Greece & Netherlands</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Yosemite National Park, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 Feb 19, 2022 – Feb 20, 2022 | 👥 Onam Bharti, Rohit Das, Kunal, Monica</div>
      <div class="trip-details">Road trip to see the Firefall</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Santa Barbara, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 Feb 12, 2022 – Feb 13, 2022 | 👥 Onam Bharti, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Carmel-by-the-Sea, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 Jan 15, 2022 – Jan 16, 2022 | 👥 Onam Bharti, Rohit Das</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2021</div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Puerto Vallarta & Boca de Tomatlan, Mexico</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Nov 21, 2021 – Nov 28, 2021 | 👥 Onam Bharti, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Santa Ynez, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 Oct 30, 2021 – Oct 31, 2021 | 👥 Rohit Das, Sumedha, Neha Vatsyayan, Siddhartha Datta</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Calgary, Banff & Jasper National Parks, Vancouver, Canada</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Aug 20, 2021 – Aug 29, 2021 | 👥 Rohit Das, Onam Bharti</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Big Island (Kona, Volcano, Hilo), HI</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Mar 21, 2021 – Mar 26, 2021 | 👥 Rohit Das, Onam Bharti</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2020</div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Lakehead (CA) & Eugene, OR</span>
        <span class="badge badge-regional">Regional / Domestic</span>
      </div>
      <div class="trip-meta">📅 Sep 3, 2020 – Sep 7, 2020 | 👥 Onam Bharti, Rohit Das, Siddhartha Datta, Sutapa Dey</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Kolkata & Bengaluru, India</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Mar 5, 2020 – Mar 18, 2020 | 👥 Rohit Das</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Cancun (Mexico) & Miami Beach, FL</span>
        <span class="badge badge-international">International / Domestic</span>
      </div>
      <div class="trip-meta">📅 Feb 8, 2020 – Feb 17, 2020 | 👥 Onam Bharti, Rohit Das</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2019</div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Pahrump, NV</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Dec 1, 2019 | 👥 Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Redding (CA) & Oregon</span>
        <span class="badge badge-regional">Regional / Domestic</span>
      </div>
      <div class="trip-meta">📅 Aug 31, 2019 – Sep 2, 2019 | 👥 Onam Bharti, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Kauai (Lihue, Kapaa, Koloa), HI</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Aug 8, 2019 – Aug 12, 2019 | 👥 Onam Bharti, Rohit Das, Meera Devi, Tarun Kumar</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Chicago, IL</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Jun 27, 2019 – Jun 28, 2019 | 👥 Solo / Unspecified</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Bothell & Oak Harbor, WA</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 May 10, 2019 – May 11, 2019 | 👥 Solo / Unspecified</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Barcelona, Seville, Granada (Spain) & Lisbon (Portugal)</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Apr 4, 2019 – Apr 15, 2019 | 👥 Onam Bharti, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">New Delhi & Kolkata, India</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Feb 23, 2019 – Mar 3, 2019 | 👥 Anusha, Meera, S N Das, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Maui (Lahaina, Hana, Kaanapali), HI</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Feb 14, 2019 – Feb 19, 2019 | 👥 Onam Bharti, Rohit Das, Varun Khandelwal, Sumedha Dharmadhikari</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2018</div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Grand Canyon Village, AZ</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Dec 30, 2018 – Jan 7, 2019 | 👥 Rohit Das, Deep Prakash Gupta</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">McArthur-Burney Falls, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 Sep 15, 2018 – Sep 16, 2018 | 👥 Rohit Das, Onam Bharti, Dhwani, Dhruvil, Varun, Sumedha, Julius, Aparna</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Las Vegas, Grand Canyon North Rim, Utah, Valley of Fire</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Aug 30, 2018 – Sep 3, 2018 | 👥 Rohit Das, Onam Bharti</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Paris (France), Bern, Grindelwald, Lauterbrunnen, Lucerne (Switzerland)</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 May 24, 2018 – Jun 3, 2018 | 👥 Onam Bharti, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Truckee & Tahoe National Forest, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 Mar 31, 2018 – Apr 1, 2018 | 👥 Onam Bharti</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">New York, Jersey City & Delhi, Mumbai (India)</span>
        <span class="badge badge-international">International / Domestic</span>
      </div>
      <div class="trip-meta">📅 Feb 17, 2018 – Feb 24, 2018 | 👥 Rohit Das, Onam Bharti</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2017</div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Bangalore, Delhi, Noida, Kolkata, Gurugram, India</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Dec 10, 2017 – Jan 1, 2018 | 👥 Onam Bharti, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Budapest, Hungary</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Oct 1, 2017 | 👥 Solo / Unspecified</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Taoyuan (Taiwan) & Bali (Indonesia)</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Sep 22, 2017 – Sep 24, 2017 | 👥 Solo / Unspecified</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Lordsburg & White Sands National Park, NM</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Jul 1, 2017 – Jul 2, 2017 | 👥 Rohit Das</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Kolkata, Delhi (India) & Alturas, CA</span>
        <span class="badge badge-international">International / Regional</span>
      </div>
      <div class="trip-meta">📅 May 13, 2017 – May 29, 2017 | 👥 Rohit Das, Shambhu Nath Das, S N Das, Siddhartha Datta</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Arizona & Las Vegas, NV</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Feb 10, 2017 – Feb 12, 2017 | 👥 Solo / Unspecified</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Carlsbad & San Diego, CA</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Jan 30, 2017 – Jan 31, 2017 | 👥 Rohit Das</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2016</div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Venice, Florence, Pisa, Cinque Terre, Rome, Vatican City</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Sep 1, 2016 – Sep 11, 2016 | 👥 Rohit Das, Onam Bharti</div>
      <div class="trip-details">Italy & Vatican City</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Vancouver & Whistler, Canada</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Jul 2, 2016 – Jul 3, 2016 | 👥 Onam Bharti</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2015</div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Bangkok, Krabi (Thailand) & Delhi, Patna, Mandarmani (India)</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Dec 11, 2015 – Jan 10, 2016 | 👥 Onam Bharti, Rohit Das, Nithin Das, S N Das</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Salt Lake City (UT) & Yellowstone / Grand Teton (WY)</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Sep 5, 2015 – Sep 8, 2015 | 👥 Meera, Onam Bharti, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">Anaheim, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 Jul 3, 2015 – Jul 5, 2015 | 👥 Rohit Das, Siddhartha Datta, Sutapa Dey</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Chicago, IL & Seattle, WA</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 May 2, 2015 – May 10, 2015 | 👥 Rohit Das, Onam Bharti</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2014</div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Raleigh/Durham, NC</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Sep 26, 2014 – Oct 5, 2014 | 👥 Rohit Das</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Cancun (Mexico) & Miami Beach, FL</span>
        <span class="badge badge-international">International / Domestic</span>
      </div>
      <div class="trip-meta">📅 Feb 8, 2014 – Feb 17, 2014 | 👥 Onam Bharti, Rohit Das</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2013</div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Dubai (UAE) & Kolkata, Delhi (India)</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Sep 12, 2013 – Oct 5, 2013 | 👥 Rohit Das, Onam Bharti</div>
    </div>

    <div class="trip-card" data-type="Regional">
      <div class="trip-header">
        <span class="trip-title">South Lake Tahoe, CA</span>
        <span class="badge badge-regional">Regional</span>
      </div>
      <div class="trip-meta">📅 Aug 10, 2013 – Aug 11, 2013 | 👥 Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">San Diego, CA</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 May 24, 2013 – May 28, 2013 | 👥 Rohit Das, Onam Bharti</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Istanbul, Nevsehir, Cappadocia (Türkiye) & Delhi (India)</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Mar 10, 2013 – Apr 2, 2013 | 👥 Onam Bharti, Rohit Das</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2012</div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Chennai, Kolkata, Patna, Delhi, India</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Oct 26, 2012 – Nov 27, 2012 | 👥 Onam Bharti, Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Phoenix, AZ & Las Vegas, NV</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Oct 3, 2012 – Oct 6, 2012 | 👥 Rohit Das, Onam Bharti</div>
      <div class="trip-details">Road trip in a convertible</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2011</div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">New York, NY & NW Arkansas</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Dec 24, 2011 – Jan 2, 2012 | 👥 Rohit Das, Shambhu Nath Das, Siddhartha Datta</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Kolkata, India</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Nov 17, 2011 – Jan 15, 2012 | 👥 Shambhu Nath Das, Rohit Das</div>
      <div class="trip-details">Rohit's Dad visiting US for the first time</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Kolkata & Chennai, India</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Feb 17, 2011 – Mar 7, 2011 | 👥 Rohit Das</div>
    </div>
  </div>

  <div class="year-section">
    <div class="year-heading">2010 & Earlier</div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Kolkata, India</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Nov 25, 2010 – Dec 20, 2010 | 👥 Rohit Das</div>
    </div>

    <div class="trip-card" data-type="International">
      <div class="trip-header">
        <span class="trip-title">Kolkata & Chennai, India</span>
        <span class="badge badge-international">International</span>
      </div>
      <div class="trip-meta">📅 Feb 13, 2009 – Mar 15, 2009 | 👥 Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Phoenix, AZ</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 Aug 17, 2007 | 👥 Rohit Das</div>
    </div>

    <div class="trip-card" data-type="Domestic">
      <div class="trip-header">
        <span class="trip-title">Federal Way & Seattle, WA</span>
        <span class="badge badge-domestic">Domestic</span>
      </div>
      <div class="trip-meta">📅 May 14, 2007 – May 15, 2007 | 👥 Rohit Das</div>
      <div class="trip-details">Summer internship while completing MS at ASU</div>
    </div>
  </div>

</div>

<script>
  // Complete list of map locations extracted from timeline entries
  const locations = [
    // 2026
    { name: "Seattle & Bellevue", lat: 47.6062, lng: -122.3321, type: "Domestic" },
    { name: "Miami Beach", lat: 25.7907, lng: -80.1300, type: "Domestic" },
    { name: "CocoCay, Bahamas", lat: 25.8186, lng: -77.9392, type: "International" },
    { name: "Buffalo & Niagara Falls", lat: 43.0962, lng: -79.0377, type: "Domestic" },
    { name: "Destin, FL", lat: 30.3935, lng: -86.4958, type: "Domestic" },
    
    // 2025
    { name: "Quito, Ecuador", lat: -0.1807, lng: -78.4678, type: "International" },
    { name: "Galápagos Islands, Ecuador", lat: -0.9538, lng: -90.9656, type: "International" },
    { name: "Bergen, Norway", lat: 60.3913, lng: 5.3221, type: "International" },
    { name: "Geiranger, Norway", lat: 62.1008, lng: 7.2059, type: "International" },
    { name: "Ålesund, Norway", lat: 62.4722, lng: 6.1495, type: "International" },
    { name: "Oslo, Norway", lat: 59.9139, lng: 10.7522, type: "International" },
    { name: "Mammoth Lakes & June Lake, CA", lat: 37.6485, lng: -118.9721, type: "Regional" },
    { name: "Red Rocks, Denver, CO", lat: 39.6654, lng: -105.2057, type: "Domestic" },
    { name: "Knights Ferry, CA", lat: 37.8188, lng: -120.6633, type: "Regional" },
    { name: "Phuket & Ao Nang, Thailand", lat: 7.8804, lng: 98.3923, type: "International" },

    // 2024
    { name: "Cabo San Lucas, Mexico", lat: 22.8905, lng: -109.9167, type: "International" },
    { name: "Barcelona, Spain", lat: 41.3851, lng: 2.1734, type: "International" },
    { name: "Reykjavik, Iceland", lat: 64.1466, lng: -21.9426, type: "International" },
    { name: "Great Smoky Mountains, TN", lat: 35.6118, lng: -83.4895, type: "Domestic" },
    { name: "Munich, Germany", lat: 48.1351, lng: 11.5820, type: "International" },
    { name: "Salzburg, Austria", lat: 47.8095, lng: 13.0550, type: "International" },
    { name: "Vienna, Austria", lat: 48.2082, lng: 16.3738, type: "International" },
    { name: "Split & Dubrovnik, Croatia", lat: 42.6507, lng: 18.0944, type: "International" },

    // 2023
    { name: "Oahu (Honolulu), HI", lat: 21.3069, lng: -157.8583, type: "Domestic" },
    { name: "Cairo & Giza, Egypt", lat: 30.0444, lng: 31.2357, type: "International" },
    { name: "Aswan & Abu Simbel, Egypt", lat: 24.0889, lng: 32.8998, type: "International" },
    { name: "Luxor, Egypt", lat: 25.6872, lng: 32.6396, type: "International" },
    { name: "Edinburgh, UK", lat: 55.9533, lng: -3.1883, type: "International" },
    { name: "London, UK", lat: 51.5074, lng: -0.1278, type: "International" },
    { name: "Fort Bragg, CA", lat: 39.4457, lng: -123.8053, type: "Regional" },
    { name: "Cappadocia & Göreme, Türkiye", lat: 38.6431, lng: 34.8289, type: "International" },
    { name: "Istanbul, Türkiye", lat: 41.0082, lng: 28.9784, type: "International" },
    { name: "Fairbanks, AK", lat: 64.8378, lng: -147.7164, type: "Domestic" },

    // 2022
    { name: "Murphys, CA", lat: 38.1377, lng: -120.4616, type: "Regional" },
    { name: "Cusco & Machu Picchu, Peru", lat: -13.1631, lng: -72.5450, type: "International" },
    { name: "Lima, Peru", lat: -12.0464, lng: -77.0428, type: "International" },
    { name: "Zion National Park, UT", lat: 37.2982, lng: -113.0263, type: "Domestic" },
    { name: "Benicia, CA", lat: 38.0494, lng: -122.1586, type: "Regional" },
    { name: "Athens, Greece", lat: 37.9838, lng: 23.7275, type: "International" },
    { name: "Santorini (Oia/Fira), Greece", lat: 36.3932, lng: 25.4615, type: "International" },
    { name: "Amsterdam, Netherlands", lat: 52.3676, lng: 4.9041, type: "International" },
    { name: "Yosemite National Park, CA", lat: 37.8651, lng: -119.5383, type: "Regional" },
    { name: "Santa Barbara, CA", lat: 34.4208, lng: -119.6982, type: "Regional" },
    { name: "Carmel-by-the-Sea, CA", lat: 36.5552, lng: -121.9233, type: "Regional" },

    // 2021
    { name: "Puerto Vallarta, Mexico", lat: 20.6534, lng: -105.2253, type: "International" },
    { name: "Santa Ynez, CA", lat: 34.6041, lng: -120.0835, type: "Regional" },
    { name: "Banff & Jasper, Canada", lat: 51.1784, lng: -115.5708, type: "International" },
    { name: "Calgary, Canada", lat: 51.0447, lng: -114.0719, type: "International" },
    { name: "Big Island (Kona/Hilo), HI", lat: 19.6399, lng: -155.9969, type: "Domestic" },

    // 2020
    { name: "Eugene, OR", lat: 44.0521, lng: -123.0868, type: "Domestic" },
    { name: "Bengaluru, India", lat: 12.9716, lng: 77.5946, type: "International" },
    { name: "Cancun, Mexico", lat: 21.1619, lng: -86.8515, type: "International" },

    // 2019 & Earlier Highlights
    { name: "Pahrump, NV", lat: 36.2083, lng: -115.9839, type: "Domestic" },
    { name: "Kauai (Lihue), HI", lat: 21.9811, lng: -159.3711, type: "Domestic" },
    { name: "Seville, Spain", lat: 37.3891, lng: -5.9845, type: "International" },
    { name: "Lisbon, Portugal", lat: 38.7223, lng: -9.1393, type: "International" },
    { name: "Maui, HI", lat: 20.7984, lng: -156.3319, type: "Domestic" },
    { name: "McArthur-Burney Falls, CA", lat: 41.0118, lng: -121.6528, type: "Regional" },
    { name: "Paris, France", lat: 48.8566, lng: 2.3522, type: "International" },
    { name: "Grindelwald, Switzerland", lat: 46.6242, lng: 8.0414, type: "International" },
    { name: "Dubai, UAE", lat: 25.2048, lng: 55.2708, type: "International" },
    { name: "Patna, India", lat: 25.5941, lng: 85.1376, type: "International" },
    { name: "Delhi, India", lat: 28.6139, lng: 77.2090, type: "International" },
    { name: "Kolkata, India", lat: 22.5726, lng: 88.3639, type: "International" },
    { name: "Chennai, India", lat: 13.0827, lng: 80.2707, type: "International" }
  ];

  // Initialize Map
  const map = L.map('travel-map').setView([20, 0], 2);

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors'
  }).addTo(map);

  // Custom Pin Color Logic
  function getMarkerColor(type) {
    if (type === 'International') return '#e53e3e'; // Red
    if (type === 'Domestic') return '#3182ce';      // Blue
    return '#38a169';                              // Green for Regional
  }

  // Add Circle Markers
  locations.forEach(loc => {
    const marker = L.circleMarker([loc.lat, loc.lng], {
      radius: 6,
      fillColor: getMarkerColor(loc.type),
      color: '#fff',
      weight: 1.5,
      opacity: 1,
      fillOpacity: 0.85
    }).addTo(map);

    marker.bindPopup(`<b>${loc.name}</b><br><span style="font-size:0.8rem; color:#666;">Category: ${loc.type}</span>`);
  });

  // Dynamic JS Filter Script
  function filterTrips(type) {
    // Button Active Styling
    const buttons = document.querySelectorAll('.filter-btn');
    buttons.forEach(btn => btn.classList.remove('active'));
    event.target.classList.add('active');

    // Filter Trip Cards
    const cards = document.querySelectorAll('.trip-card');
    cards.forEach(card => {
      const cardType = card.getAttribute('data-type');
      if (type === 'all' || cardType.includes(type)) {
        card.style.display = 'block';
      } else {
        card.style.display = 'none';
      }
    });

    // Hide Empty Year Headings
    const yearSections = document.querySelectorAll('.year-section');
    yearSections.forEach(section => {
      const visibleCards = section.querySelectorAll('.trip-card[style="display: block;"], .trip-card:not([style*="display"])');
      let hasVisible = false;
      visibleCards.forEach(c => {
        if (c.style.display !== 'none') hasVisible = true;
      });
      section.style.display = hasVisible ? 'block' : 'none';
    });
  }
</script>
