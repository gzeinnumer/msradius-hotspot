# SIMPLE

Gunakan Login Page kami sebagai login page anda dan silahkan ubah logonya

# TETAP GUNAKAN LOGIN PAGE SAYA

jika kamu tetap mau gunakan halaman Login Page kamu, cukup paste kodingan kami ke login page kami,

## List EVoucher

<p align="center">
  <img src="/img/img4.png" width="400"/>
</p>

```
<!-- LIST EVOUCHER START-->
<p class="info">Buy Evoucher</p>
<div id="evoucher-list" class="evoucher-list"></div>
<script>
    async function loadEvouchers() {
        try {
            const response = await fetch('https://dev.msradius.com/api/evoucher');
            if (response.ok) {
                const res = await response.json();

                const evoucherList = document.getElementById('evoucher-list');
                var v = "";
                //for (let index = res.data.length-1; index >= 0; index--) { // Buat Urutan Jadi terbalik
                for (let index = 0; index < res.data.length; index++) {
                    const element = res.data[index];
                    //Gunakan ini untuk menghilang beberapa profile, gunakan ID sebagai patokan, contoh
                    // if(element.id == 14 || element.id == 15){
                    //     continue;
                    // }
                    v += `
                        <div class="voucher-card">
                            <div class="voucher-details">
                                <h3>${element.id} -  ${element.profile_name}</h3>
                                <p><strong>Time Limit : </strong> ${element.time_limit}</p>
                                <p><strong>Quota Limit : </strong> ${element.quota_limit}</p>
                                <p><strong>Active Period : </strong> ${element.active_period}</p>
                                <p><strong>Price : </strong> ${element.price_sell.toLocaleString()}</p>
                            </div>
                            <div class="button-group">
                                <a href="https://dev.msradius.com/store?unique=${element.id}" class="btn-buy-bulk" target="_blank">Buy +++</a>
                            </div>
                        </div>
                    `;
                    // <a href="https://dev.msradius.com/store?unique=${element.id}&profiles=1,1,1" class="btn-buy-bulk" target="_blank">Buy +++</a>
                    // untuk membatasi profile yang muncul di login page, bisa pakai if atau profiles=1,1,1 info lebih lanjut ke admin
                }
                evoucherList.innerHTML = v;
            } else {
                console.error('Failed to fetch e-vouchers:', response.status);
            }
        } catch (error) {
            console.error('Error fetching e-vouchers:', error);
        }
    }

    window.onload = loadEvouchers;
</script>
<p class="info">Powered by MSRadius &copy; 2024</p>
<!-- LIST EVOUCHER END-->
```

## REGISTER MEMBER

<p align="center">
  <img src="/img/img3.png" width="400"/>
</p>

```
<!-- REGISTER MEMBER START-->
<p class="info">Register Member</p>
<p class="info">Silahkan daftar untuk dapat menggunakan firut Whatsapp BOT dari penyedia jasa intenet sebagai Membership</p>
<form id="registerForm">
    <label>
        <img class="ico" src="img/whatsapp.svg" alt="#" />
        <input name="whatsapp" type="number" placeholder="Whatsapp" />
    </label>
    <label>
        <img class="ico" src="img/name.svg" alt="#" />
        <input name="name" type="text" placeholder="Name" />
    </label>
    <label>
        <img class="ico" src="img/home.svg" alt="#" />
        <input name="address" type="text" placeholder="Address" />
    </label>
    <input type="submit" value="Register" />
</form>
<script>
    document.getElementById('registerForm').addEventListener('submit', async function (e) {
        e.preventDefault();
        const form = this;
        const formData = new FormData(this);
        const data = {
            whatsapp: formData.get('whatsapp'),
            name: formData.get('name'),
            address: formData.get('address')
        };

        try {
            const response = await fetch('https://dev.msradius.com/api/registermember', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(data)
            });

            if (response.ok) {
                const result = await response.json();
                if(result.code == 200){
                    form.reset();
                    alert('Registration successful!');
                }else{
                    alert(result.msg);
                }
            } else {
                alert('Failed to register.');
            }
        } catch (error) {
            console.error('Error:', error);
            alert('An error occurred. Please try again.');
        }
    });
</script>
<!-- REGISTER MEMBER END-->
```

## CHECK VOUCHER

<p align="center">
  <img src="/img/img2.png" width="400"/>
</p>

```
<!-- CHECK STATUS START-->
<p class="info">Check Status</p>
<p class="info">Silahkan masukan username mengecheck status voucher.</p>
<form id="checkForm">
    <label>
        <img class="ico" src="img/voucher.svg" alt="#" />
        <input name="unique" type="text" placeholder="Username" />
    </label>
    <input type="submit" value="Check" />
</form>
<script>
    document.getElementById('checkForm').addEventListener('submit', async function (e) {
        e.preventDefault();
        const form = this;
        const formData = new FormData(this);

        try {
            const response = await fetch('https://dev.msradius.com/api/checkusername?unique=' + formData.get('unique'), {
                method: 'GET',
                headers: {
                    'Content-Type': 'application/json'
                },
            });

            if (response.ok) {
                const result = await response.json();
                if (result.code == 200) {
                    alert(result.msg);
                } else {
                    alert(result.msg);
                }
            } else {
                alert('No Data Username.');
            }
        } catch (error) {
            console.error('Error:', error);
            alert('An error occurred. Please try again.');
        }
    });
</script>
<!-- CHECK STATUS END-->
```

## OPTIMIZE VOUCHER

<p align="center">
  <img src="/img/img1.png" width="400"/>
</p>

```
<!-- OPTIMIZE START-->
<p class="info">Optimize Username</p>
<p class="info">Silahkan masukan username untuk memperbaiki username yang tidak bisa login sebelum expired.</p>
<form id="optimizeForm">
    <label>
        <img class="ico" src="img/voucher.svg" alt="#" />
        <input name="unique" type="text" placeholder="Username" />
    </label>
    <input type="submit" value="Optimize" />
</form>
<script>
    document.getElementById('optimizeForm').addEventListener('submit', async function (e) {
        e.preventDefault();
        const form = this;
        const formData = new FormData(this);

        try {
            const response = await fetch('https://dev.msradius.com/api/optimizeusername?unique='+ formData.get('unique'), {
                method: 'GET',
                headers: {
                    'Content-Type': 'application/json'
                },
            });

            if (response.ok) {
                const result = await response.json();
                if (result.code == 200) {
                    form.reset();
                    alert('Optimize successful! please try login again');
                } else {
                    alert('Failed to Optimize.');
                }
            } else {
                alert('Failed to Optimize.');
            }
        } catch (error) {
            console.error('Error:', error);
            alert('An error occurred. Please try again.');
        }
    });
</script>
<!-- OPTIMIZE END-->
```

# STYLE

```
<link rel="stylesheet" href="css/style-ms.css">
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

/ip firewall address-list add list=gopay_walled_garden address=gopay.co.id
/ip firewall address-list add list=gopay_walled_garden address=api.gopay.co.id
/ip firewall address-list add list=gopay_walled_garden address=midtrans.com
/ip hotspot walled-garden ip add action=accept src-address-list=gopay_walled_garden
```
