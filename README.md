# SIMPLE

Gunakan Login Page kami sebagai login page anda dan silahkan ubah logonya

# TETAP GUNAKAN LOGIN PAGE SAYA

jika kamu tetap mau gunakan halaman Login Page kamu, cukup paste kodingan kami ke login page kami,

```html
<style>
  /* Evoucher STYLE */
  .evoucher-list {
    max-width: 600px;
    margin: auto;
    font-family: Arial, sans-serif;
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .voucher-card {
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    background-color: rgba(255, 255, 255, 0.8);
    display: flex;
    justify-content: space-between;
  }

  .voucher-details {
    flex: 1;
    padding-right: 10px;
  }

  .voucher-details h3 {
    margin: 0 0 8px;
    font-size: 20px;
    color: #333;
  }

  .voucher-details p {
    margin: 4px 0;
    color: #666;
  }

  .button-group {
    display: flex;
    flex-direction: column;
    gap: 10px;
    align-items: flex-end;
  }

  .btn-buy-one,
  .btn-buy-bulk {
    text-decoration: none;
    padding: 10px 15px;
    color: #fff;
    border-radius: 4px;
    transition: background-color 0.3s ease;
    font-size: 14px;
    width: 100px;
    /* Adjust button width */
    text-align: center;
  }

  .btn-buy-one {
    background: #3e4d59;
    border-radius: 16px;
  }

  .btn-buy-one:hover {
    background: #3e4d59;
    border-radius: 16px;
  }

  .btn-buy-bulk {
    background: #3e4d59;
    border-radius: 16px;
  }

  .btn-buy-bulk:hover {
    background: #3e4d59;
    border-radius: 16px;
  }

  /* E VOUCHER STYLE END */
</style>
```

```html
<p class="info">Buy Evoucher</p>
<div id="evoucher-list" class="evoucher-list"></div>

<script>
  async function loadEvouchers() {
    var url = "dev.msradius.com";
    try {
      const response = await fetch("https://" + url + "/api/evoucher");
      if (response.ok) {
        const res = await response.json();

        const evoucherList = document.getElementById("evoucher-list");
        var v = "";
        for (let index = 0; index < res.data.length; index++) {
          const element = res.data[index];
          console.log(element);
          v +=
            `
                        <div class="voucher-card">
                            <div class="voucher-details">
                                <h3>${element.profile_name}</h3>
                                <p><strong>Time Limit : </strong> ${
                                  element.time_limit
                                }</p>
                                <p><strong>Quota Limit : </strong> ${
                                  element.quota_limit
                                }</p>
                                <p><strong>Active Period : </strong> ${
                                  element.active_period
                                }</p>
                                <p><strong>Price : </strong> ${element.price_sell.toLocaleString()}</p>
                            </div>
                            <div class="button-group">
                                <a href="https://` +
            url +
            `/store?unique=${element.id}&qty=1" class="btn-buy-one" target="_blank">Buy 1</a>
                                <a href="https://` +
            url +
            `/store?unique=${element.id}" class="btn-buy-bulk" target="_blank">Buy +++</a>
                            </div>
                        </div>
                    `;
        }
        evoucherList.innerHTML = v;
      } else {
        console.error("Failed to fetch e-vouchers:", response.status);
      }
    } catch (error) {
      console.error("Error fetching e-vouchers:", error);
    }
  }

  window.onload = loadEvouchers;
</script>

<p class="info">Powered by MSRadius &copy; 2024</p>
```

# walled-garden

```
/ip hotspot walled-garden ip
add action=accept disabled=no comment="MS-MSRADIUS" dst-host="demo.msradius.com";
add action=accept disabled=no comment="MS-DUITKU" dst-host="duitku.com";
add action=accept disabled=no comment="MS-MIDTRANS" dst-host="midtrans.com";
add action=accept disabled=no comment="MS-MIDTRANS" dst-host="app.sandbox.midtrans.com";
add action=accept disabled=no comment="MS-MIDTRANS" dst-host="app.midtrans.com";
add action=accept disabled=no comment="MS-MIDTRANS" dst-host="cloudfront.net";
add action=accept disabled=no comment="MS-MIDTRANS" dst-host="d2f3dnusg0rbp7.cloudfront.net";
add action=accept disabled=no comment="MS-MIDTRANS" dst-host="bam.nr-data.net";
add action=accept disabled=no comment="MS-MIDTRANS" dst-host="snap-web-raccoon-integration.gojekapi.com";
add action=accept disabled=no comment="MS-MIDTRANS GOPAY" dst-host="api.midtrans.com";
add action=accept disabled=no comment="MS-MIDTRANS GOPAY" dst-host="gopay.co.id";
add action=accept disabled=no comment="MS-MIDTRANS GOPAY" dst-host="snap.midtrans.com";
add action=accept disabled=no comment="MS-MIDTRANS GOPAY" dst-host="payment.midtrans.com";
add action=accept disabled=no comment="MS-DANA" dst-host="m.dana.id";
add action=accept disabled=no comment="MS-DANA" dst-host="dana.id";
add action=accept disabled=no comment="MS-DANA" dst-host="split.io";
add action=accept disabled=no comment="MS-DANA" dst-host="sdk.split.io";
add action=accept disabled=no comment="MS-DANA" dst-host="auth.split.io";
add action=accept disabled=no comment="MS-DANA" dst-host="events.split.io";
add action=accept disabled=no comment="MS-DANA" dst-host="a.m.dana.id";
add action=accept disabled=no comment="MS-DANA" dst-host="mas-log1.saas.dana.id";
add action=accept disabled=no comment="MS-DANA" dst-host="api-js.mixpanel.com";
add action=accept disabled=no comment="MS-DANA" dst-host="captcha.saas.dana.id";
add action=accept disabled=no comment="MS-DANA" dst-host="dana-assets-id.oss-ap-southeast-5.aliyuncs.com";
```
