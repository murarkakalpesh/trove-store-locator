<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Trove Store Locator</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; padding: 20px; background-color: #f5f5f5; }
    h2 { text-align: center; color: #333; }
    .container { max-width: 500px; margin: auto; background: #fff; padding: 20px; border-radius: 10px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
    input { width: 100%; padding: 12px; margin-bottom: 15px; border-radius: 5px; border: 1px solid #ccc; font-size: 16px; }
    .store-card { display: none; background: #e0f7fa; margin-bottom: 10px; padding: 15px; border-radius: 8px; box-shadow: 0 2px 6px rgba(0,0,0,0.1); }
    .store-card.active { display: block; background: #b2ebf2; }
    .store-name { font-size: 18px; font-weight: bold; margin-bottom: 5px; }
    .store-address { font-size: 16px; margin-bottom: 3px; }
    .store-pincode { font-size: 14px; color: #555; margin-bottom: 5px; }
    .store-link a { color: #007BFF; text-decoration: none; font-size: 14px; }
    .store-link a:hover { text-decoration: underline; }
    .no-store { display: none; text-align: center; color: red; font-weight: bold; margin-top: 10px; }
  </style>
</head>
<body>

  <h2>Trove Store Locator</h2>
  <div class="container">
    <input type="text" id="pincodeInput" placeholder="Enter your Pincode">

    <div id="storeList">
      <div class="store-card" data-pincode="400001">
        <div class="store-name">Trove Store 1</div>
        <div class="store-address">123 Main Street, Mumbai</div>
        <div class="store-pincode">Pincode: 400001</div>
        <div class="store-link"><a href="https://www.google.com/maps/place/123+Main+Street,+Mumbai" target="_blank">View on Map</a></div>
      </div>
      <div class="store-card" data-pincode="400002">
        <div class="store-name">Trove Store 2</div>
        <div class="store-address">456 Park Avenue, Mumbai</div>
        <div class="store-pincode">Pincode: 400002</div>
        <div class="store-link"><a href="https://www.google.com/maps/place/456+Park+Avenue,+Mumbai" target="_blank">View on Map</a></div>
      </div>
      <div class="store-card" data-pincode="411001">
        <div class="store-name">Trove Store 3</div>
        <div class="store-address">789 Central Road, Pune</div>
        <div class="store-pincode">Pincode: 411001</div>
        <div class="store-link"><a href="https://www.google.com/maps/place/789+Central+Road,+Pune" target="_blank">View on Map</a></div>
      </div>
    </div>

    <div class="no-store" id="noStore">No store found for this pincode.</div>
  </div>

  <script>
    const input = document.getElementById('pincodeInput');
    const stores = document.querySelectorAll('.store-card');
    const noStore = document.getElementById('noStore');

    input.addEventListener('keyup', function() {
      const filter = input.value.trim();
      let found = false;
      stores.forEach(store => {
        if (store.dataset.pincode.includes(filter) && filter !== '') {
          store.classList.add('active');
          found = true;
        } else {
          store.classList.remove('active');
        }
      });
      noStore.style.display = found ? 'none' : 'block';
    });
  </script>

</body>
</html>
