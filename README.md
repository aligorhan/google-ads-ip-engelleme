# google-ads-ip-engelleme
Google Ads sahte tıklama (click fraud) önleme ve IP engelleme sistemi. Bot trafiğini tespit eder, şüpheli IP’leri otomatik engeller ve Google Ads IP listesi limitini (500) akıllıca yönetir. Supabase, Edge Functions ve captcha (reCAPTCHA/Turnstile) ile entegre çalışır.

# Google Ads Click Fraud Önleme & IP Engelleme Sistemi

Google Ads kampanyalarındaki **sahte tıklama (click fraud)** ve **bot trafiğini** tespit edip **otomatik IP engelleme** yapan kapsamlı bir anti-fraud motoru. Şüpheli IP’leri Google Ads IP Exclusion listesine senkronlar ve **500 IP limitini** dolmadan akıllıca yönetir.

## Özellikler

- **Bot / sahte tıklama tespiti** için esnek kurallar
- Şüpheli IP’leri **otomatik engelleme** (Google Ads IP Exclusion)
- **IP listesi limiti (500)** için otomatik yönetim  
  - `synced_with_ads=true` kayıt sayısı **490**’a ulaşınca en eski **10 IP** Google Ads listesinden kaldırılır  
  - Veritabanında bu kayıtlar `synced_with_ads=false` olarak güncellenir  
- Supabase tabanlı kayıt ve kontrol akışı
- Captcha doğrulama desteği:
  - **reCAPTCHA v3**
  - **Cloudflare Turnstile**
- Kampanya / hesap düzeyinde farklı versiyonlarla genişletilebilir mimari

## Mimari Notlar

Bu repo, Google Ads IP engelleme sürecini otomatikleştirmek için aşağıdaki bileşenlere dayanır:

- **Google Ads API (OAuth 2.0)**
- **Supabase** (veri saklama + edge functions / serverless iş mantığı)
- İsteğe bağlı captcha doğrulama (reCAPTCHA / Turnstile)

> Not: Google Ads API kullanımında `DEVELOPER_TOKEN`, `MCC_ID`, `CUSTOMER_ID` gibi kritik bilgiler gerekir.

## Kurulum

1. Repoyu klonla:
