# Smart Photo Tools — किए गए सुधारों की सूची (2026-09-22)

यह फ़ाइल सिर्फ़ आपकी जानकारी के लिए है। इसे repo में डालना ज़रूरी नहीं है (चाहें तो `notes/` फ़ोल्डर में रख सकते हैं)।

## ✅ ठीक किए गए Critical Bugs

1. **`guides.html` → `guide.html`**
   हर पेज के header nav और footer में यह link 404 दे रहा था। 22 फ़ाइलों में ठीक किया।

2. **Related-Guides widgets में 6 टूटे हुए links**
   `index.html` और 6 tool पेजों (aadhaar, compressor, passport, photoresizer, signature, voterid) पर
   गलत filenames की जगह असली guide फ़ाइलों से जोड़ा गया:
   - `aadhaar-photo-upload-error.html` → `guide-upload-error.html`
   - `photo-kb-kaise-kam-kare.html` → `guide-kb-kam.html`
   - `signature-photo-kaise-banaye.html` → `guide-exam-photo-signature.html`
   - `passport-size-photo-rules.html` → `guide-passport-photo.html`
   - `pixel-kb-dpi-difference.html` → `guide-pixel-kb-dpi.html`
   - `photo-reject-hone-ke-karan.html` → `guide-photo-privacy.html` (सबसे नज़दीकी मौजूदा लेख; caption भी असली content से मैच करने के लिए बदला)

3. **`sitemap.xml` पूरा दोबारा बनाया**
   पुराने sitemap में 9 URLs किसी असली फ़ाइल से मेल नहीं खाते थे (जैसे `pan-photo.html`), और
   ~20 असली पेज (about, contact, privacy, disclaimer, terms, guides, blog) शामिल ही नहीं थे।
   अब सभी 29 असली पेज सही URL, priority और आज की तारीख के साथ मौजूद हैं।

   ⚠️ **ज़रूरी:** 6 blog article फ़ाइलों (`passport-photo-guide.html` आदि) का canonical tag
   `/blog/...` path इस्तेमाल करता है। कृपया कन्फर्म करें कि repo में ये फ़ाइलें
   `blog/` नाम के subfolder के अंदर ही हैं — वरना sitemap और internal links टूट जाएंगे।

4. **Blog section homepage से जुड़ा नहीं था (orphan pages)**
   सभी 22 मुख्य पेजों के footer में "Blog" link जोड़ा गया।

5. **Open Graph / Twitter Card tags 21 पेजों पर पूरी तरह गायब थे**
   WhatsApp/Facebook पर link share करने पर कोई preview नहीं दिखता था। अब सभी 30 पेजों में
   og:title, og:description, og:url, og:image, twitter:card जोड़े गए।
   एक नया branded `og-image.png` (1200×630) बनाया गया है — इसे repo root में डालना न भूलें।

6. **blog.html में canonical tag / OG tags गायब थे** — जोड़े गए। साथ ही इसका रंग (purple gradient)
   बाकी site के brand colors (navy/blue) से बदलकर एक जैसा किया गया।

7. **15 पेजों पर AdSense script `<meta charset>` से पहले लोड हो रहा था**
   (technical best-practice issue) — सभी में सही क्रम में move किया गया।

## 📋 आपके लिए Manual Steps

- [ ] ये फ़ाइलें GitHub repo में commit/push करें (मौजूदा फ़ाइलों को overwrite करें)
- [ ] `og-image.png` को repo root में upload करना न भूलें
- [ ] कन्फर्म करें कि 6 blog article फ़ाइलें `blog/` subfolder में ही हैं
- [ ] Google Search Console में नया sitemap.xml दोबारा submit करें ("Sitemaps" सेक्शन में)
- [ ] कुछ दिन बाद Search Console की "Pages" रिपोर्ट देखें कि पुराने 404 errors साफ़ हो गए या नहीं

## 💡 भविष्य के लिए सुझाव (अभी नहीं किया गया)

- blog.html और blog articles का layout/design बाकी site के design-system से पूरी तरह मैच कराना
  (अभी सिर्फ़ रंग बदले हैं, structure अलग है)
- हर tool के लिए एक अलग, ज़्यादा specific og-image बनाना (अभी एक ही generic image सभी पेजों पर है)
- होमपेज पर दो अलग "उपयोगी Guide" sections हैं जो कुछ guides को दोहराते हैं — चाहें तो एक में मिला सकते हैं
