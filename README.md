---
description: Dokumentasi API Batong App. Belum fix masih bisa berubah
---

# Batong API Documentation

## E-Commerce

Figma :   
[https://www.figma.com/file/CjvLnon7sAZZ4TEh9163is/Batong-Prototype?node-id=457%3A1269](https://www.figma.com/file/CjvLnon7sAZZ4TEh9163is/Batong-Prototype?node-id=457%3A1269)

Requirements : [https://docs.google.com/document/d/1pg4pn5dQTBx2mAs2vTc\_4r78ucwsWh5Ud6SVCCm2Brg/edit?usp=sharing](https://docs.google.com/document/d/1pg4pn5dQTBx2mAs2vTc_4r78ucwsWh5Ud6SVCCm2Brg/edit?usp=sharing)

### 🧑🏻‍💼 **Penjual** <a id="penjual"></a>

* **Penjual dapat membuat, melihat, dan mengupdate produk ✅**
* **Penjual dapat melihat semua pesanan dan detail pesanan produk yang masuk ✅**
* **Penjual dapat melihat analitik dari hasil penjualan produk : rata-rata rating toko, pendapatan total, total penjualan setiap bulan ✅**
* **Penjual dapat melihat analitik persebaran demografi dari pembeli produk ✅**

{% api-method method="get" host="batong.id" path="/api/penjual/analitik-toko" %}
{% api-method-summary %}
Lihat Analitik Toko
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk melihat analitik toko : pesanan selesai, produk dilihat, produk terpopuler
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "pesananSelesai" : 200,
    "produkDilihat" : 999,
    "produkTerpopuler": "kain andi",
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="batong.id" path="/api/penjual/produk" %}
{% api-method-summary %}
Lihat Semua Produk
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk melihat semua produk
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[ 
    { 
        "kodeProduk": "PR001", 
        "namaProduk": "Kain Andi", 
        "variasi": "Baju",
        "status" : "Ready Stock",
        "gambarProduk" : ["url(gambar/produk/{produkId}/1)", "url(gambar/produk/{produkId}/2", ... ]                      
        "harga": 135000,
        "deskripsi" : "lorem ipsum blablabla",
        "stock": 111,
        "penjualan": 5,
        "impresi" : 1000,
        "isJual" : true,
    } 
]

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="batong.id" path="/api/penjual/produk/:kodeProduk" %}
{% api-method-summary %}
Lihat Detail Produk
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk melihat deta
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="kodeProduk" type="string" required=true %}
Kode Produk
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{ 
    "kodeProduk": "PR001", 
    "namaProduk": "Kain Andi", 
    "variasi": "Baju",
    "status" : "Ready Stock",
    "gambarProduk" : ["url(gambar/produk/{produkId}/1)", "url(gambar/produk/{produkId}/2", ... ]                      
    "harga": 135000,
    "deskripsi" : "lorem ipsum blablabla",
    "stock": 111,
    "penjualan": 5,
    "impresi" : 1000,
    "isJual" : true,
  } 
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="batong.id" path="/api/penjual/produk" %}
{% api-method-summary %}
Tambah Produk Baru Ke Toko
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk menambahkan produk baru
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="kodeProduk" type="string" required=false %}
Kode Produk
{% endapi-method-parameter %}

{% api-method-parameter name="namaProduk" type="string" required=true %}
Nama Produk
{% endapi-method-parameter %}

{% api-method-parameter name="fotoProduk" type="array" required=true %}
Foto Produk
{% endapi-method-parameter %}

{% api-method-parameter name="keterangan" type="string" required=false %}
Keterangan
{% endapi-method-parameter %}

{% api-method-parameter name="ketersediaanProduk" type="string" required=true %}
Ketersediaan Produk
{% endapi-method-parameter %}

{% api-method-parameter name="kategori" type="string" required=true %}
Kategori Produk
{% endapi-method-parameter %}

{% api-method-parameter name="harga" type="number" required=true %}
Harga Produk
{% endapi-method-parameter %}

{% api-method-parameter name="stock" type="integer" required=true %}
Stock Produk
{% endapi-method-parameter %}

{% api-method-parameter name="penjualan" type="integer" required=true %}
Jumlah Penjualan Produk
{% endapi-method-parameter %}

{% api-method-parameter name="impresi" type="integer" required=true %}
Impresi Produk
{% endapi-method-parameter %}

{% api-method-parameter name="isJual" type="boolean" required=true %}
Status Produk
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
  { 
    "kodeProduk": "PR001", 
    "namaProduk": "Kain Andi", 
    "variasi": "Baju",
    "status" : "Ready Stock",
    "gambarProduk" : ["url(gambar/produk/{produkId}/1)", "url(gambar/produk/{produkId}/2", ... ]                      
    "harga": 135000,
    "deskripsi" : "lorem ipsum blablabla",
    "stock": 111,
    "penjualan": 5,
    "impresi" : 1000,
    "isJual" : true,
  } 
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="batong.id" path="/api/penjual/produk/:kodeProduk" %}
{% api-method-summary %}
Update Status Produk
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk mengupdate status produk : dijual atau tidak
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="kodeProduk" type="string" required=true %}
Kode Produk
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="isJual" type="boolean" required=true %}
Status Produk
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
  { 
    "kodeProduk": "PR001", 
    "namaProduk": "Kain Andi", 
    "variasi": "Baju",
    "status" : "Ready Stock",
    "gambarProduk" : ["url(gambar/produk/{produkId}/1)", "url(gambar/produk/{produkId}/2", ... ]                      
    "harga": 135000,
    "deskripsi" : "lorem ipsum blablabla",
    "stock": 111,
    "penjualan": 5,
    "impresi" : 1000,
    "isJual" : true,
  } 
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="batong.id" path="/api/penjual/pesanan" %}
{% api-method-summary %}
Lihat Semua Pesanan
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk lihat semua pesanan yang masuk
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "statusPesanan" : "semua", //opsi status pesanan : semua, belum dibayar, perlu diproses, dikirim, selesai, dll.
        "kodePesanan" : "PR001",
        "produk" :  {
                        "kodeProduk": "PR001", 
                        "namaProduk": "Kain Andi", 
                        "variasi": "Baju", 
                        "harga": 135000, 
                        "stock": 111, 
                        "penjualan": 5,
                        "impresi" : 1000,
                        "isJual" : false,
                    },
        "kuantitas" : 2,
        "pengiriman" : "JNE",
        "akasi" : "tolak",        
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="batong.id" path="/api/penjual/pesanan/:kodePesanan" %}
{% api-method-summary %}
Lihat Detail Pesanan
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk melihat detail pesanan
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
 {
        "statusPesanan" : "semua", //opsi status pesanan : semua, belum dibayar, perlu diproses, dikirim, selesai, dll.
        "kodePesanan" : "PR001",
        "produk" :  {
                        "kodeProduk": "PR001", 
                        "namaProduk": "Kain Andi", 
                        "variasi": "Baju", 
                        "harga": 135000, 
                        "stock": 111, 
                        "penjualan": 5,
                        "impresi" : 1000,
                        "isJual" : false,
                    },
        "kuantitas" : 2,
        "dataCustomer" : {
                            "namaDepan" : "Mbah",
                            "namaBelakang": "Batong",
                            "alamatEmail": "mbahtong@gmail.com",
                            "nomorTelepon": "08111111111",
                            "alamat": "Jln. jalan aja, RT01/01",
                            "kota": "Depok",
                            "negara": "Indonesia",
                            "kodePos" "1234",
                         },
        "metodeBayar" : "transfer bank",
        "catatanPengiriman" : "tolong packing yang benar",
        "pengiriman" : "JNE",
        "akasi" : "tolak",        
    }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="batong.id" path="/api/penjual/gambaran-umum" %}
{% api-method-summary %}
Lihat Analitik Penjualan Umum Toko
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk melihat analitik penjualan toko
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "rating" :4.5,
    "pendapatan" : [
        {
            "bulan" : "2021-07",
            "penjualan": 550000,
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="batong.id" path="/api/penjual/demografi-pembeli" %}
{% api-method-summary %}
Lihat Demografi Pembeli
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk melihat demografi pembeli
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    {
        "profilePembeli" : {
                                "nama" : "putri",
                                "alamat" : "Jakarta",
                            }
                            
    },
    {
        "profilePembeli" : {
                                "nama" : "putra",
                                "alamat" : "Jakarta"
                            }
                            
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



### 🙎🏻 Pembeli

* Pembeli dapat melihat produk dan detail produk yang dijual **✅**
* Pembeli dapat melihat, menambahkan, mengupdate produk ke keranjang belanja **✅**
* Pembeli dapat membuat dan melihat pesanan **✅**

{% api-method method="get" host="batong.id" path="/api/pembeli/produk" %}
{% api-method-summary %}
Lihat Semua Produk
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk melihat semua produk
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
    { 
      "namaToko" : "Sari Kenongo",
      "produk"   : [ 
                        { 
                            "id": 1, 
                            "namaProduk": "Kain Andi", 
                            "variasi": "Baju", 
                            "harga": 135000, 
                            "stock": 111, 
                        },
                        ...
                   ]
    },
    ...
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="batong.id" path="/api/pembeli/produk/:kodeProduk" %}
{% api-method-summary %}
Lihat Detail Produk
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk melihat detail produk
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="kodeProduk" type="string" required=true %}
Kode Produk
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
 { 
    "kodeProduk":"PR001", 
    "namaProduk": "Kain Andi", 
    "variasi": "Baju", 
    "harga": 135000,
    "deskripsi" : "lorem ipsum blablabla",
    "stock": 111,
  } 
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="batong.id" path="/api/pembeli/produk/:kodeProduk/buat-pesanan" %}
{% api-method-summary %}
Tambah Pesanan produk
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk menambahkan pesanan produk
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="kodeProduk" type="string" required=true %}
Kode Produk
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="produk" type="object" required=true %}
Produk Pesanan
{% endapi-method-parameter %}

{% api-method-parameter name="kuantitas" type="integer" required=true %}
Kuantitas Pesanan
{% endapi-method-parameter %}

{% api-method-parameter name="dataCustomer" type="object" required=true %}
Data Customer
{% endapi-method-parameter %}

{% api-method-parameter name="metodeBayar" type="string" required=true %}
Metode Pembayaran
{% endapi-method-parameter %}

{% api-method-parameter name="catatan" type="string" required=false %}
Catatan Pemesanan
{% endapi-method-parameter %}

{% api-method-parameter name="pengiriman" type="string" required=true %}
Metode Pengiriman
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{ 
        "produk" :  {
                        "id": 1, 
                        "namaProduk": "Kain Andi", 
                        "variasi": "Baju", 
                        "harga": 135000, 
                        "stock": 111, 
                        "penjualan": 5,
                        "impresi" : 1000,
                        "isJual" : false,
                    },
        "kuantitas"    : 2,
        "dataCustomer" : {
                            "namaDepan" : "Mbah",
                            "namaBelakang": "Batong",
                            "alamatEmail": "mbahtong@gmail.com",
                            "nomorTelepon": "08111111111",
                            "alamat": "Jln. jalan aja, RT01/01",
                            "kota": "Depok",
                            "negara": "Indonesia",
                            "kodePos" "1234",
                         },
        "metodeBayar" : "transfer bank",
        "catatan"     : "tolong packing yang benar",
        "pengiriman"  : "JNE",
}  
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="batong.id" path="/api/pembeli/pesanan" %}
{% api-method-summary %}
Lihat Pesanan
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk melihat semua pesanan dibuat
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
        { 
                "produk" :  {
                                "kodeProduk": "PR001", 
                                "namaProduk": "Kain Andi", 
                                "variasi": "Baju", 
                                "harga": 135000, 
                                "stock": 111, 
                                "penjualan": 5,
                                "impresi" : 1000,
                                "isJual" : false,
                            },
                "kuantitas"    : 2,
                "dataCustomer" : {
                                    "namaDepan" : "Mbah",
                                    "namaBelakang": "Batong",
                                    "alamatEmail": "mbahtong@gmail.com",
                                    "nomorTelepon": "08111111111",
                                    "alamat": "Jln. jalan aja, RT01/01",
                                    "kota": "Depok",
                                    "negara": "Indonesia",
                                    "kodePos" "1234",
                                 },
                "metodeBayar" : "transfer bank",
                "catatan"     : "tolong packing yang benar",
                "pengiriman"  : "JNE",
        },
        ...
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="batong.id" path="/api/pembeli/keranjang-belanja" %}
{% api-method-summary %}
Lihat Keranjang Belanja
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk melihat keranjang belanja 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
        { 
                "produk" :  {
                                "kodeProduk": "PR001", 
                                "namaProduk": "Kain Andi", 
                                "variasi": "Baju", 
                                "harga": 135000, 
                                "stock": 111, 
                                "penjualan": 5,
                                "impresi" : 1000,
                                "isJual" : false,
                            },
                "kuantitas"    : 2,
                "catatan"     : "tolong packing yang benar",
        },
        ...
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="batong.id" path="/api/pembeli/:kodeProduk/tambahkan-ke-keranjang" %}
{% api-method-summary %}
Tambah Produk Ke Keranjang Belanja
{% endapi-method-summary %}

{% api-method-description %}
API Endpoint untuk menambahkan produk ke keranjang belanja
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="kodeProduk" type="string" required=true %}
Kode Produk
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="produk" type="object" required=false %}
Produk
{% endapi-method-parameter %}

{% api-method-parameter name="kuantitas" type="integer" required=false %}
Kuantitas Produk
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{ 
        "produk" :  {
                        "kodeProduk": "PR001", 
                        "namaProduk": "Kain Andi", 
                        "variasi": "Baju", 
                        "harga": 135000, 
                        "stock": 111, 
                        "penjualan": 5,
                        "impresi" : 1000,
                        "isJual" : false,
                    },
        "kuantitas"  : 1, //default : 1
},
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

