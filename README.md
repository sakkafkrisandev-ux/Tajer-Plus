# Tajer-Plus
Tajer Plus is an AI-powered marketing platform designed to help small businesses and local stores create professional product advertisements easily. Users can upload product images, enter product details and prices, generate attractive marketing content in Arabic, and create ready-to-share promotional designs for WhatsApp and social 

<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#101827">
  <title>تاجر بلس | مساعدك التسويقي</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: Tahoma, Arial, sans-serif;
      background: #f3f5f9;
      color: #172033;
    }

    header {
      background: #101827;
      color: white;
      padding: 22px 16px;
    }

    .header-inner {
      max-width: 760px;
      margin: auto;
    }

    .brand {
      font-size: 25px;
      font-weight: bold;
    }

    .brand span {
      color: #5ee0b5;
    }

    header p {
      color: #c5cfdd;
      font-size: 14px;
      line-height: 1.8;
      margin-bottom: 0;
    }

    main {
      max-width: 760px;
      margin: 22px auto;
      padding: 0 14px 35px;
    }

    .card {
      background: white;
      padding: 18px;
      margin-bottom: 17px;
      border-radius: 16px;
      box-shadow: 0 4px 18px #1522380a;
    }

    h2 {
      font-size: 18px;
      margin-top: 0;
    }

    label {
      display: block;
      font-size: 14px;
      font-weight: bold;
      margin: 15px 0 7px;
    }

    input, textarea, select {
      width: 100%;
      padding: 12px;
      border: 1px solid #d9dfeb;
      border-radius: 10px;
      background: white;
      font: inherit;
      font-size: 15px;
    }

    textarea {
      resize: vertical;
      min-height: 78px;
    }

    input:focus, textarea:focus {
      outline: 2px solid #91e8d0;
      border-color: #159b78;
    }

    button {
      font: inherit;
      font-weight: bold;
      border: 0;
      border-radius: 10px;
      padding: 13px;
      cursor: pointer;
    }

    .primary {
      background: #087f63;
      color: white;
      width: 100%;
      margin-top: 16px;
    }

    .secondary {
      background: #e7f7f1;
      color: #08664f;
      width: 100%;
      margin-top: 10px;
    }

    .muted {
      color: #667085;
      font-size: 13px;
      line-height: 1.8;
    }

    #photoPreview {
      display: none;
      width: 100%;
      max-height: 240px;
      object-fit: contain;
      margin-top: 12px;
      border-radius: 12px;
      background: #f5f6f8;
    }

    #results {
      display: none;
    }

    .poster {
      background: #132b2a;
      color: white;
      border-radius: 14px;
      overflow: hidden;
      text-align: center;
    }

    .poster img {
      display: none;
      width: 100%;
      max-height: 320px;
      object-fit: contain;
      background: #fff;
    }

    .poster-copy {
      padding: 22px 16px;
    }

    .poster h3 {
      font-size: 24px;
      margin: 6px 0 12px;
      overflow-wrap: anywhere;
    }

    #posterDescription {
      white-space: pre-wrap;
      line-height: 1.9;
      overflow-wrap: anywhere;
    }

    #posterPrice {
      color: #6ff0c7;
      font-size: 22px;
      font-weight: bold;
      margin: 15px 0;
    }

    .result-box {
      background: #f4f7fa;
      border-radius: 12px;
      padding: 14px;
      margin-top: 12px;
      line-height: 1.9;
      overflow-wrap: anywhere;
    }

    .result-box button {
      background: #e1e9f2;
      color: #172033;
      margin-top: 8px;
      padding: 9px 13px;
    }

    footer {
      text-align: center;
      padding: 10px;
      color: #667085;
      font-size: 12px;
    }
  </style>
</head>

<body>
  <header>
    <div class="header-inner">
      <div class="brand">تاجر <span>بلس +</span></div>
      <p>حوّل منتجات متجرك إلى إعلانات جاهزة للنشر.</p>
    </div>
  </header>

  <main>
    <section class="card">
      <h2>🏪 معلومات المتجر</h2>

      <label for="storeName">اسم متجرك</label>
      <input id="storeName" placeholder="مثال: متجر الأناقة">

      <label for="productName">اسم المنتج</label>
      <input id="productName" placeholder="مثال: عطر فاخر">

      <label for="price">السعر</label>
      <input id="price" type="number" min="0"
        step="any" placeholder="مثال: 2500">

      <label for="currency">العملة</label>
      <select id="currency">
        <option value="ريال يمني">ريال يمني</option>
        <option value="ريال سعودي">ريال سعودي</option>
        <option value="دولار">دولار</option>
        <option value="بدون عملة">بدون عملة</option>
      </select>

      <label for="details">معلومات حقيقية عن المنتج</label>
      <textarea id="details"
        placeholder="اكتب اللون أو الحجم أو المميزات المؤكدة"></textarea>

      <label for="productPhoto">صورة المنتج</label>
      <input id="productPhoto" type="file"
        accept="image/*">

      <img id="photoPreview" alt="معاينة صورة المنتج">

      <p class="muted">
        ارفع صورة المنتج الأصلية. لا ترفع صورًا لا تملك حق استخدامها.
      </p>

      <button class="primary" id="generateBtn">
        ✨ أنشئ الإعلان
      </button>
    </section>

    <section class="card" id="results">
      <h2>🎨 معاينة الإعلان</h2>

      <div class="poster" id="poster">
        <img id="posterImage" alt="صورة المنتج في الإعلان">

        <div class="poster-copy">
          <div id="posterStore"></div>
          <h3 id="posterTitle"></h3>
          <div id="posterDescription"></div>
          <div id="posterPrice"></div>
          <div>للطلب والاستفسار تواصل مع المتجر</div>
        </div>
      </div>

      <button class="primary" id="downloadBtn">
        تنزيل الإعلان كصورة
      </button>

      <h2 style="margin-top:24px">📝 نصوص التسويق</h2>

      <div class="result-box">
        <strong>وصف المنتج</strong>
        <p id="descriptionText"></p>
        <button data-copy="descriptionText">نسخ الوصف</button>
      </div>

      <div class="result-box">
        <strong>حالة واتساب</strong>
        <p id="whatsappText"></p>
        <button data-copy="whatsappText">نسخ الحالة</button>
      </div>

      <div class="result-box">
        <strong>عنوان إعلاني بديل</strong>
        <p id="alternativeText"></p>
        <button data-copy="alternativeText">نسخ العنوان</button>
      </div>

      <p class="muted">
        راجع النص والسعر قبل نشر الإعلان.
      </p>
    </section>

    <section class="card">
      <h2>📌 ما الذي نبنيه الآن؟</h2>
      <p class="muted">
        هذه نسخة أولية تعمل داخل المتصفح. توليد النصوص فيها يعتمد
        على قوالب برمجية، وليس على نموذج ذكاء اصطناعي متصل بعد.
        الخطوة التالية هي إضافة الذكاء الاصطناعي وحفظ المنتجات.
      </p>
    </section>
  </main>

  <footer>
    تاجر بلس © 2026 — النسخة التجريبية
  </footer>

  <script>
    const $ = id => document.getElementById(id);

    let photoData = "";

    $("productPhoto").addEventListener("change", event => {
      const file = event.target.files[0];

      photoData = "";
      $("photoPreview").style.display = "none";

      if (!file) return;

      if (!file.type.startsWith("image/")) {
        alert("اختر ملف صورة صالحًا.");
        event.target.value = "";
        return;
      }

      if (file.size > 5 * 1024 * 1024) {
        alert("حجم الصورة أكبر من 5 ميجابايت.");
        event.target.value = "";
        return;
      }

      const reader = new FileReader();

      reader.onload = () => {
        photoData = reader.result;
        $("photoPreview").src = photoData;
        $("photoPreview").style.display = "block";
      };

      reader.readAsDataURL(file);
    });

    $("generateBtn").addEventListener("click", () => {
      const store = $("storeName").value.trim();
      const name = $("productName").value.trim();
      const priceInput = $("price").value.trim();
      const details = $("details").value.trim();
      const currency = $("currency").value;

      if (!store || !name || !priceInput) {
        alert("اكتب اسم المتجر واسم المنتج والسعر أولًا.");
        return;
      }

      const price = Number(priceInput);

      if (!Number.isFinite(price) || price < 0) {
        alert("تحقق من السعر الذي أدخلته.");
        return;
      }

      const formattedPrice =
        new Intl.NumberFormat("ar").format(price);

      const priceText = currency === "بدون عملة"
        ? formattedPrice
        : formattedPrice + " " + currency;

      const description = details
        ? name + "\n" + details
        : "تعرّف على " + name + " من " + store + ".";

      const whatsapp =
        "✨ " + name + "\n" +
        (details ? details + "\n" : "") +
        "السعر: " + priceText + "\n" +
        "للاستفسار، تواصل مع " + store + ".";

      const alternative =
        "اكتشف " + name + " لدى " + store;

      $("posterStore").textContent = store;
      $("posterTitle").textContent = name;
      $("posterDescription").textContent = details;
      $("posterPrice").textContent = priceText;

      $("descriptionText").textContent = description;
      $("whatsappText").textContent = whatsapp;
      $("alternativeText").textContent = alternative;

      $("posterImage").style.display = photoData
        ? "block" : "none";

      if (photoData) {
        $("posterImage").src = photoData;
      }

      $("results").style.display = "block";
      $("results").scrollIntoView({
        behavior: "smooth",
        block: "start"
      });
    });

    document.querySelectorAll("[data-copy]").forEach(button => {
      button.addEventListener("click", async () => {
        const text = $(button.dataset.copy).textContent;

        try {
          await navigator.clipboard.writeText(text);
          alert("تم نسخ النص.");
        } catch {
          const area = document.createElement("textarea");
          area.value = text;
          document.body.appendChild(area);
          area.select();

          const copied = document.execCommand("copy");
          area.remove();

          alert(copied ? "تم نسخ النص." :
            "تعذر النسخ. حدّد النص وانسخه يدويًا.");
        }
      });
    });

    $("downloadBtn").addEventListener("click", async () => {
      try {
        const module = await import(
          "https://cdn.jsdelivr.net/npm/html-to-image@1.11.13/+esm"
        );

        const dataUrl = await module.toPng($("poster"), {
          pixelRatio: 2,
          cacheBust: true
        });

        const link = document.createElement("a");
        link.download = "tajer-plus-ad.png";
        link.href = dataUrl;
        link.click();
      } catch (error) {
        alert("تعذر إنشاء الصورة. تحقق من اتصال الإنترنت ثم حاول مجددًا.");
      }
    });
  </script>
</body>
</html>
