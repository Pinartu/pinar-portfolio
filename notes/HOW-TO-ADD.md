# Notes & Tools — how to add content

Bu klasör senin içerik merkezin. İki tür içerik var: **Posts** (LinkedIn'den uyarlanan yazılar) ve **Tools** (araç önerileri). Hiç kod bilmene gerek yok — sadece kopyala-yapıştır.

---

## A) Yeni bir TOOL (araç) eklemek — en hızlısı

1. `notes/index.html` dosyasını aç.
2. İçinde `▼▼▼ NEW CARD HERE` yazan satırı bul.
3. Aşağıdaki bloğu o satırın **hemen altına** yapıştır ve içini değiştir:

```html
<a class="card tool" data-type="tool" href="ARACIN_LINKI" target="_blank" rel="noopener">
  <span class="tag tool">Tool · KATEGORI</span>
  <h2>Aracın Adı</h2>
  <p class="excerpt">Tek-iki cümle: ne işe yarıyor, sen neden kullanıyorsun.</p>
  <div class="meta">Ücretsiz / Ücretli · Web</div>
  <span class="arrow">Visit tool →</span>
</a>
```

Kaydet. Bitti — araç listede görünür ve "Tools" filtresine düşer.

---

## B) Yeni bir POST (yazı) eklemek — 3 adım

**Adım 1 — Yazı sayfasını oluştur**
- `notes/_TEMPLATE.html` dosyasını kopyala.
- Kopyayı yeniden adlandır: `konu-basligi.html`
  (küçük harf, kelimeler arası tire `-`, boşluk yok — bu URL olur).
- Dosyayı aç, içindeki tüm `{{...}}` yerlerini doldur. İpucu: dosyada `{{` ara, hepsini bulursun.
- Yazının gövdesini `<article>` bölümünün içine yaz.

**Adım 2 — Hub'a kart ekle**
- `notes/index.html` içinde `▼▼▼ NEW CARD HERE` satırını bul, altına şunu yapıştır:

```html
<a class="card post" data-type="post" href="/notes/konu-basligi.html">
  <span class="tag post">Post · KONU</span>
  <h2>Yazının başlığı (merak uyandıran)</h2>
  <p class="excerpt">1-2 cümlelik özet.</p>
  <div class="meta"><time datetime="2026-06-20">Jun 20, 2026</time> · 4 min read</div>
  <span class="arrow">Read the note →</span>
</a>
```
- `href` ile `_TEMPLATE`'ten verdiğin dosya adının **aynı** olduğundan emin ol.

**Adım 3 — Google görsün diye sitemap'e ekle**
- Ana klasördeki `sitemap.xml` dosyasını aç.
- Son `</url>` ile `</urlset>` arasına şunu ekle:

```xml
<url>
  <loc>https://pinar-portfolio-mu.vercel.app/notes/konu-basligi.html</loc>
  <lastmod>2026-06-20</lastmod>
  <changefreq>monthly</changefreq>
  <priority>0.7</priority>
</url>
```

Kaydet, siteyi yayınla. Tamam.

---

## SEO için küçük hatırlatmalar
- Her postun `<title>` ve `meta description`'ı **farklı** olsun — Google'da çıkan metin budur.
- Başlığa hedef anahtar kelimeyi koy (örn. "EU AI Act", "Shopify SEO").
- Sayfada **tek bir `<h1>`** olsun (şablonda zaten öyle); ara başlıklar `<h2>`.
- Yeni postu yazınca ana sayfadan ya da ilgili başka bir posttan ona link ver — iç linkler SEO'ya yarar.
- İlk örnek post: `eu-ai-act-article-4-readiness.html` — örnek olarak inceleyebilirsin.
