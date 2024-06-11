
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مترجم اللغة</title>
</head>
<body>
    <h1>مترجم اللغة</h1>
    <label for="sourceLanguage">من :</label>
    <select id="sourceLanguage">
        <option value="arabic">العربية</option>
        <option value="abstop">ABSTOP</option>
    </select><br>

    <label for="targetLanguage">الى :</label>
    <select id="targetLanguage">
        <option value="arabic">العربية</option>
        <option value="abstop">ABSTOP</option>
    </select><br>

    <label for="sourceText">النص الأصلي:</label><br>
    <input type="text" id="sourceText" name="sourceText"><br>
    <button onclick="translateText()">ترجم</button><br>
    <label for="translatedText">النص المترجم:</label><br>
    <textarea id="translatedText" name="translatedText" rows="4" cols="50" readonly></textarea><br>

    <script>
        function translateText() {
            var sourceText = document.getElementById("sourceText").value;
            var sourceLanguage = document.getElementById("sourceLanguage").value;
            var targetLanguage = document.getElementById("targetLanguage").value;

            var translatedText = translate(sourceText, sourceLanguage, targetLanguage);
            document.getElementById("translatedText").value = translatedText;
        }

        function translate(text, sourceLang, targetLang) {
            const translationMapArabicToAbstop = {
                'ض': 'ص',
                'ص': 'ث',
                'ث': 'ق',
                'ق': 'ف',
                'ف': 'غ',
                'غ': 'ع',
                'ع': 'ه',
                'ه': 'خ',
                'خ': 'ح',
                'ح': 'ج',
                'ج': 'ض',
                'ش': 'س',
                'س': 'ي',
                'ي': 'ب',
                'ب': 'ل',
                'ل': 'ا',
                'ا': 'ت',
                'ت': 'ن',
                'ن': 'م',
                'م': 'ك',
                'ك': 'ط',
                'ط': 'ش',
                'ذ': 'ء',
                'ء': 'ؤ',
                'ؤ': 'ر',
                'ر': 'ى',
                'ى': 'ة',
                'ة': 'و',
                'و': 'ز',
                'ز': 'ظ',
                'ظ': 'د',
                'د': 'ذ'
            };

            const translationMapAbstopToArabic = {
                'ص': 'ض',
                'ث': 'ص',
                'ق': 'ث',
                'ف': 'ق',
                'غ': 'ف',
                'ع': 'غ',
                'ه': 'ع',
                'خ': 'ه',
                'ح': 'خ',
                'ج': 'ح',
                'ض': 'ج',
                'س': 'ش',
                'ي': 'س',
                'ب': 'ي',
                'ل': 'ب',
                'ا': 'ل',
                'ت': 'ا',
                'ن': 'ت',
                'م': 'ن',
                'ك': 'م',
                'ط': 'ك',
                'ش': 'ط',
                'ء': 'ذ',
                'ؤ': 'ء',
                'ر': 'ؤ',
                'ى': 'ر',
                'ة': 'ى',
                'و': 'ة',
                'ز': 'و',
                'ظ': 'ز',
                'د': 'ظ',
                'ذ': 'د'
            };

            var translationMap;
            if (sourceLang === 'arabic' && targetLang === 'abstop') {
                translationMap = translationMapArabicToAbstop;
            } else if (sourceLang === 'abstop' && targetLang === 'arabic') {
                translationMap = translationMapAbstopToArabic;
            } else {
                return 'لم يتم تحديد اللغة بشكل صحيح';
            }

            var translatedText = "";
            for (var i = 0; i < text.length; i++) {
                if (translationMap[text[i]] !== undefined) {
                    translatedText += translationMap[text[i]];
                } else {
                    translatedText += text[i];
                }
            }
            return translatedText;
        }
    </script>
</body>
