<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<title>Sana Bir Mektup Var</title>

<style>
    body {
        margin: 0;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        background: #fff;
        font-family: Arial, sans-serif;
        text-align: center;
    }

    .container {
        cursor: pointer;
    }

    .title {
        font-size: 22px;
        margin-bottom: 10px;
    }

    .heart {
        font-size: 28px;
        margin-bottom: 10px;
    }

    .name {
        font-size: 18px;
        margin-bottom: 20px;
    }

    /* ZARF */
    .envelope {
        position: relative;
        width: 140px;
        height: 90px;
        margin: auto;
    }

    .envelope .body {
        width: 100%;
        height: 100%;
        background: #f2f2f2;
        border: 2px solid #ccc;
        border-radius: 4px;
        position: relative;
        z-index: 1;
    }

    .envelope .flap {
        position: absolute;
        top: 0;
        left: 0;
        width: 0;
        height: 0;
        border-left: 70px solid transparent;
        border-right: 70px solid transparent;
        border-bottom: 50px solid #e0e0e0;
        transform-origin: top;
        transition: transform 0.8s;
        z-index: 2;
    }

    .envelope.open .flap {
        transform: rotateX(180deg);
    }

    .hint {
        font-size: 14px;
        color: #555;
        margin-top: 10px;
    }

    /* MEKTUP */
    .letter {
        display: none;
        font-size: 18px;
        line-height: 1.6;
        max-width: 280px;
        white-space: pre-line;
    }

    .cursor {
        display: inline-block;
        width: 2px;
        background: black;
        animation: blink 1s infinite;
        margin-left: 3px;
    }

    @keyframes blink {
        0%, 50%, 100% { opacity: 1; }
        25%, 75% { opacity: 0; }
    }
</style>
</head>

<body>

<div class="container" onclick="openEnvelope()">

    <div id="before">
        <div class="title">Sana Bir Mektup Var</div>
        <div class="heart">❤️</div>
        <div class="name">Araf</div>

        <div class="envelope" id="envelope">
            <div class="flap"></div>
            <div class="body"></div>
        </div>

        <div class="hint">Açmak için zarfa tıkla...</div>
    </div>

    <div class="letter" id="letter">
        <span id="text"></span><span class="cursor"></span>
    </div>

</div>

<script>
const message = `❤️

Sevgili irem:
Bu akşamki tartışma yüzünden özür dilerim.
Ben senin yanlış yapmandan endişelenmemiştim elbiseden dolayıda bi endişem yoktu sana yakışacağına emindim neden onları söyledim bilmiyorum “düşündüğümden daha iyi olmuş” dediğimde düşündüğüm şeylerden yanlış bahsettim. dediğin doğru kendimle çeliştim ama her iki çelişme durumunda da seni düşündüm yaptığım hataydı farkındayım ve zaten bu hatalar yüzünden hep mağdur düşüyorum. Elimde olan bi durum değil gibi, bu yüzdende beni affetmeni beklemiyorum, sana iyi gelmek isterken daha da kötü hissettirdim ama bilerek değildi. Böyle biri olmama ne sebep oldu bilmiyorum kararları net sözü tek biriydim ama son zamanlarda kendimden şüphe duyuyorum. Bu durumdayken sana da iyi gelemiyorum sanırım, bu vazgeçtiğimin haberi değil bu sadece bir adım geriye attığımı söylemenin bi yolu ben hala burda olacağım ama daha fazla yaklaşamayacağım çünkü bu haldeyken yaklaşırsam sana iyi hissettirmeyebilirim. Yaptıklarımdan dediklerimden utandım mesajlara baktığımda bunları ben mi dedim dedirtti resmen. Fotoğrafların silindi için rahat olsun elbisende çok güzel hayırlı olsun güle güle giy inşallah. Yine herşey söz verdiğim gibi sadece biraz geride durmam gerektiğini düşünüyorum halen bi konuda konuşmak yada yardım almak istersen burdayım. Hala seni seviyorum ve saygını koruyacağım. Ben iyi değilim sebebini bulup çözeceğim ama biraz zamana ihtiyacım olabilir. Karanlık biyerde gibiyim yeni olmadı ama yeni etkisini gösteriyor. Tekrar özür dilerim sana bunu yaşatmak istememiştim. Kendine iyi bak görüşmek dileğiyle, goodbyy… ♾️♥️
let index = 0;

function typeText() {
    if (index < message.length) {
        document.getElementById("text").innerHTML += message.charAt(index);
        index++;
        setTimeout(typeText, 50);
    }
}

function openEnvelope() {
    const env = document.getElementById("envelope");
    env.classList.add("open");

    setTimeout(() => {
        document.getElementById("before").style.display = "none";
        document.getElementById("letter").style.display = "block";
        typeText();
    }, 900);
}
</script>

</body>
</html>
