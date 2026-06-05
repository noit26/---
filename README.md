[index.2.html](https://github.com/user-attachments/files/28623563/index.2.html)
# ---<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>戦国城主タイプ診断｜城×MBTI風</title>
  <style>
    :root {
      --bg: #f5efe6;
      --ink: #2b2118;
      --main: #7a3e1d;
      --main-dark: #5f2f15;
      --card: #ffffff;
      --soft: #fff7e8;
      --line: #e4d6c2;
      --muted: #6b6259;
    }

    * {
      box-sizing: border-box;
    }

    body {
      font-family: "Hiragino Sans", "Yu Gothic", "Meiryo", sans-serif;
      background: var(--bg);
      color: var(--ink);
      margin: 0;
      line-height: 1.7;
    }

    header {
      background:
        linear-gradient(rgba(43,33,24,0.78), rgba(43,33,24,0.88)),
        radial-gradient(circle at top left, #9a5a2d, #2b2118 60%);
      color: white;
      padding: 48px 20px;
      text-align: center;
    }

    header h1 {
      margin: 0 0 10px;
      font-size: clamp(28px, 5vw, 44px);
      letter-spacing: 0.04em;
    }

    header p {
      margin: 0;
      opacity: 0.92;
    }

    main {
      max-width: 880px;
      margin: 32px auto;
      padding: 0 16px 48px;
    }

    .card {
      background: var(--card);
      border-radius: 18px;
      padding: 24px;
      box-shadow: 0 8px 24px rgba(0,0,0,0.12);
      margin-bottom: 22px;
    }

    .lead {
      font-size: 16px;
      color: var(--muted);
    }

    .pill {
      display: inline-block;
      padding: 6px 12px;
      border-radius: 999px;
      background: var(--soft);
      border: 1px solid var(--line);
      color: var(--main);
      font-weight: bold;
      font-size: 13px;
      margin: 4px 4px 4px 0;
    }

    .question {
      margin-bottom: 26px;
      padding-bottom: 20px;
      border-bottom: 1px solid var(--line);
    }

    .question p {
      font-weight: bold;
      font-size: 17px;
      margin-bottom: 12px;
    }

    label {
      display: block;
      margin: 10px 0;
      padding: 13px 14px;
      background: #f8f4ee;
      border: 1px solid transparent;
      border-radius: 12px;
      cursor: pointer;
      transition: 0.15s;
    }

    label:hover {
      background: #eadfce;
      border-color: #d4b896;
    }

    input[type="radio"] {
      transform: scale(1.15);
      margin-right: 8px;
    }

    textarea, input[type="text"] {
      width: 100%;
      min-height: 48px;
      padding: 12px;
      border: 1px solid var(--line);
      border-radius: 12px;
      font-size: 16px;
      font-family: inherit;
      background: #fffdf9;
    }

    textarea {
      min-height: 84px;
      resize: vertical;
    }

    button {
      width: 100%;
      padding: 16px;
      border: none;
      border-radius: 14px;
      background: var(--main);
      color: white;
      font-size: 18px;
      font-weight: bold;
      cursor: pointer;
      transition: 0.15s;
    }

    button:hover {
      background: var(--main-dark);
      transform: translateY(-1px);
    }

    .sub-button {
      margin-top: 10px;
      background: #2b2118;
      font-size: 15px;
    }

    .sub-button:hover {
      background: #17110c;
    }

    #result {
      display: none;
      margin-top: 28px;
      padding: 26px;
      background: var(--soft);
      border: 2px solid var(--main);
      border-radius: 18px;
    }

    .type-name {
      font-size: clamp(26px, 5vw, 38px);
      font-weight: bold;
      color: var(--main);
      line-height: 1.35;
      margin-bottom: 8px;
    }

    .type-code {
      font-weight: bold;
      color: white;
      background: var(--main);
      display: inline-block;
      padding: 6px 12px;
      border-radius: 999px;
      margin-bottom: 18px;
    }

    .result-grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 14px;
    }

    .result-box {
      background: #fffdf8;
      border: 1px solid var(--line);
      border-radius: 14px;
      padding: 16px;
    }

    .result-box h3 {
      margin: 0 0 8px;
      color: var(--main);
    }

    .bars {
      margin-top: 18px;
      display: grid;
      gap: 12px;
    }

    .bar-row {
      background: #fffdf8;
      border: 1px solid var(--line);
      border-radius: 12px;
      padding: 12px;
    }

    .bar-label {
      display: flex;
      justify-content: space-between;
      font-size: 14px;
      font-weight: bold;
      margin-bottom: 6px;
    }

    .bar {
      width: 100%;
      height: 12px;
      background: #e9dccb;
      border-radius: 999px;
      overflow: hidden;
    }

    .bar-fill {
      height: 100%;
      width: 50%;
      background: var(--main);
      border-radius: 999px;
    }

    .copy-area {
      white-space: pre-wrap;
      background: #2b2118;
      color: white;
      border-radius: 14px;
      padding: 16px;
      font-size: 14px;
      overflow-x: auto;
    }

    .small {
      font-size: 13px;
      color: var(--muted);
      text-align: center;
      margin-top: 18px;
    }

    footer {
      text-align: center;
      padding: 24px;
      color: var(--muted);
      font-size: 13px;
    }
  </style>
</head>
<body>
  <header>
    <h1>戦国城主タイプ診断</h1>
    <p>城の好みから、あなたの“城主としての性格”を診断します。</p>
  </header>

  <main>
    <section class="card">
      <span class="pill">城×MBTI風</span>
      <span class="pill">16タイプ診断</span>
      <span class="pill">Claude深掘り対応</span>
      <p class="lead">
        質問に答えると、あなたを「戦国時代の城主タイプ」として診断します。
        診断後に表示される文章をClaudeに貼ると、さらに個別分析できます。
      </p>
    </section>

    <form id="quizForm" class="card">
      <div class="question">
        <p>Q1. あなたが一番惹かれる城は？</p>
        <label><input type="radio" name="q1" value="I" required> 山奥にそびえる、簡単には近づけない山城</label>
        <label><input type="radio" name="q1" value="E"> 城下町までにぎわう、人が集まる平城</label>
        <label><input type="radio" name="q1" value="N"> 雲海に浮かぶような、ロマン全振りの天空の城</label>
        <label><input type="radio" name="q1" value="S"> 石垣・堀・門がしっかり残る実用的な城</label>
      </div>

      <div class="question">
        <p>Q2. 城に一番必要だと思うものは？</p>
        <label><input type="radio" name="q2" value="J" required> 計算された縄張りと防御計画</label>
        <label><input type="radio" name="q2" value="P"> 状況に応じて動ける柔軟さ</label>
        <label><input type="radio" name="q2" value="T"> 勝つための合理性</label>
        <label><input type="radio" name="q2" value="F"> 人が安心して暮らせる空気</label>
      </div>

      <div class="question">
        <p>Q3. 兵糧攻めされたらどうする？</p>
        <label><input type="radio" name="q3" value="I" required> 静かに耐えて、相手が焦るのを待つ</label>
        <label><input type="radio" name="q3" value="E"> 周囲を巻き込んで援軍や交渉ルートを探す</label>
        <label><input type="radio" name="q3" value="T"> 損得を計算して最も合理的な判断をする</label>
        <label><input type="radio" name="q3" value="F"> 家臣や民を守る選択を最優先にする</label>
      </div>

      <div class="question">
        <p>Q4. 家臣に一番求めるものは？</p>
        <label><input type="radio" name="q4" value="J" required> 決めたことをやり切る安定感</label>
        <label><input type="radio" name="q4" value="P"> その場で動ける機転</label>
        <label><input type="radio" name="q4" value="T"> 実力と判断力</label>
        <label><input type="radio" name="q4" value="F"> 忠誠心と人間味</label>
      </div>

      <div class="question">
        <p>Q5. 城下町に置きたいものは？</p>
        <label><input type="radio" name="q5" value="E" required> みんなが集まる酒場</label>
        <label><input type="radio" name="q5" value="S"> 生活を支える商店街</label>
        <label><input type="radio" name="q5" value="I"> 静かに過ごせる庭園や森</label>
        <label><input type="radio" name="q5" value="N"> 毎月なにかが起きる祭りの広場</label>
      </div>

      <div class="question">
        <p>Q6. 攻めるならどんな攻め方？</p>
        <label><input type="radio" name="q6" value="T" required> 勝ち筋を分析して一気に崩す</label>
        <label><input type="radio" name="q6" value="F"> できれば戦わず、話し合いで落とす</label>
        <label><input type="radio" name="q6" value="J"> 作戦を立てて予定通り進める</label>
        <label><input type="radio" name="q6" value="P"> 相手の隙を見てアドリブで動く</label>
      </div>

      <div class="question">
        <p>Q7. 好きな城の見どころは？</p>
        <label><input type="radio" name="q7" value="S" required> 石垣・堀・門などのリアルな構造</label>
        <label><input type="radio" name="q7" value="N"> 歴史のロマンや物語</label>
        <label><input type="radio" name="q7" value="T"> 防御の合理性や戦略</label>
        <label><input type="radio" name="q7" value="F"> そこで暮らした人の気配</label>
      </div>

      <div class="question">
        <p>Q8. 自分の城を一言で表すなら？</p>
        <label><input type="radio" name="q8" value="I" required> 秘密基地</label>
        <label><input type="radio" name="q8" value="E"> にぎやかな拠点</label>
        <label><input type="radio" name="q8" value="J"> 完成された要塞</label>
        <label><input type="radio" name="q8" value="P"> 変化し続ける城</label>
      </div>

      <div class="question">
        <p>任意：好きな城や理由があれば書いてください</p>
        <input type="text" id="favoriteCastle" placeholder="例：松本城、竹田城、大阪城など" />
        <textarea id="freeReason" placeholder="例：黒い天守がかっこいい、山城の不便さが逆にロマン、石垣が好き など"></textarea>
      </div>

      <button type="submit">診断する</button>
    </form>

    <section id="result">
      <div class="type-name" id="typeName"></div>
      <div class="type-code" id="typeCode"></div>

      <div class="result-grid">
        <div class="result-box">
          <h3>性格・特徴</h3>
          <p id="description"></p>
        </div>
        <div class="result-box">
          <h3>強み</h3>
          <p id="strength"></p>
        </div>
        <div class="result-box">
          <h3>弱点</h3>
          <p id="weakness"></p>
        </div>
        <div class="result-box">
          <h3>向いている城</h3>
          <p id="castle"></p>
        </div>
        <div class="result-box">
          <h3>現代での生態</h3>
          <p id="modern"></p>
        </div>
        <div class="result-box">
          <h3>最後に一言</h3>
          <p id="message"></p>
        </div>
      </div>

      <div class="bars">
        <div class="bar-row">
          <div class="bar-label"><span>山城型 I</span><span>城下町型 E</span></div>
          <div class="bar"><div class="bar-fill" id="barIE"></div></div>
        </div>
        <div class="bar-row">
          <div class="bar-label"><span>実務型 S</span><span>ロマン型 N</span></div>
          <div class="bar"><div class="bar-fill" id="barSN"></div></div>
        </div>
        <div class="bar-row">
          <div class="bar-label"><span>軍師型 T</span><span>人情型 F</span></div>
          <div class="bar"><div class="bar-fill" id="barTF"></div></div>
        </div>
        <div class="bar-row">
          <div class="bar-label"><span>築城計画型 J</span><span>遊撃型 P</span></div>
          <div class="bar"><div class="bar-fill" id="barJP"></div></div>
        </div>
      </div>

      <button class="sub-button" id="copyBtn" type="button">Claude用プロンプトをコピーする</button>
      <div class="result-box" style="margin-top:14px;">
        <h3>Claudeに貼る用</h3>
        <div class="copy-area" id="claudePrompt"></div>
      </div>
    </section>

    <p class="small">※この診断はエンタメです。正式なMBTI診断ではありません。</p>
  </main>

  <footer>
    戦国城主タイプ診断｜GitHub Pages対応版
  </footer>

  <script>
    const form = document.getElementById("quizForm");
    const resultSection = document.getElementById("result");
    const copyBtn = document.getElementById("copyBtn");

    const results = {
      INTJ: {
        name: "孤高山城軍師型",
        castle: "備中松山城、岩村城、七尾城",
        description: "人を簡単に入れない山城のように、慎重で戦略的。表では静かでも、頭の中ではかなり先まで縄張りを引いています。",
        strength: "長期戦・設計・構造化に強く、混乱した場でも冷静に勝ち筋を探せます。",
        weakness: "防御線を張りすぎて、味方まで入城審査で止まることがあります。",
        modern: "少人数の深い会話が好き。グループLINEでは静かでも、裏で完璧な作戦メモを作っています。",
        message: "その山城、強い。でもたまには城門を開けよう。"
      },
      INTP: {
        name: "縄張り研究者型",
        castle: "姫路城、彦根城、松山城",
        description: "なぜその堀があるのか、なぜ道が曲がるのかを考え続けるタイプ。城を見ているようで、実は構造そのものを愛しています。",
        strength: "複雑なものを面白がり、誰も気づかない仕組みに気づけます。",
        weakness: "考え始めると築城が終わらず、家臣が『殿、完成はいつですか』となりがち。",
        modern: "会議中に本質的な一言を放つタイプ。ただし話し出すまでに少し時間がかかります。",
        message: "敵より先に、味方が縄張り解説で迷子です。"
      },
      ENTJ: {
        name: "総構え統率型",
        castle: "江戸城、大阪城、名古屋城",
        description: "城単体ではなく、城下町・経済・人材まで含めて天下を取りにいくタイプ。スケールの大きさが武器です。",
        strength: "人を動かし、資源を集め、大きな計画を前に進める力があります。",
        weakness: "城が大きくなりすぎて、たまに家臣の休憩所が消えます。",
        modern: "プロジェクトを立ち上げるのが得意。気づいたら周囲が役職についています。",
        message: "あなたの城下町、絶対に月1で経営会議があります。"
      },
      ENTP: {
        name: "奇策遊撃城主型",
        castle: "小田原城、上田城、忍城",
        description: "真正面から守るより、相手が嫌がる方法を考えるタイプ。アイデアと口のうまさで戦場をかき回します。",
        strength: "発想力と機転があり、ピンチをゲームのように面白がれます。",
        weakness: "作戦が面白すぎて、家臣が理解する前に次の作戦へ行きがち。",
        modern: "企画会議で急に場を変える人。雑談から新規事業を生みます。",
        message: "その奇策、好き。でも議事録は残して。"
      },
      INFJ: {
        name: "静謐理想城主型",
        castle: "松本城、犬山城、郡上八幡城",
        description: "静かな美しさと深い思想を持つタイプ。城は守るためだけでなく、ありたい世界を形にする場所だと考えます。",
        strength: "人の気持ちや場の空気を読み、長期的な理想に向かって進めます。",
        weakness: "理想が深すぎて、家臣が『つまり何をすれば？』となることがあります。",
        modern: "少人数で深い話をするのが好き。飲み会の後半で急に核心を突きます。",
        message: "その天守、静かだけど思想が強い。"
      },
      INFP: {
        name: "ロマン山城詩人型",
        castle: "竹田城、苗木城、津和野城",
        description: "便利さよりも物語や景色に惹かれるタイプ。城を見て、構造より先に『ここに生きた人』を想像します。",
        strength: "共感力と想像力があり、人の心を動かす言葉を持っています。",
        weakness: "現実の補給線を忘れて、ロマンだけで山頂に城を建てがち。",
        modern: "好きなものを語ると急に目が輝く。実はかなり熱量があります。",
        message: "兵糧は少ない。でも物語は満ちている。"
      },
      ENFJ: {
        name: "城下町プロデューサー型",
        castle: "大阪城、熊本城、会津若松城",
        description: "人が集まり、物語が生まれる場をつくるタイプ。城主というより、城下町全体の空気を育てる人です。",
        strength: "周囲を励まし、巻き込み、みんなで前に進む力があります。",
        weakness: "人のために動きすぎて、自分の本丸が手薄になりがち。",
        modern: "イベント運営やチームづくりが得意。気づくと相談が集まってきます。",
        message: "あなたの城、たぶん人が帰りたがりません。"
      },
      ENFP: {
        name: "祭り城下町型",
        castle: "高松城、今治城、松江城",
        description: "城は守るだけでなく、人が出会い楽しむ場所。にぎわいと偶然を愛する、開放感のある城主です。",
        strength: "場を明るくし、初対面の人同士を自然につなげます。",
        weakness: "祭りを増やしすぎて、会計奉行が泣く可能性があります。",
        modern: "人を誘うのが上手い。気づいたら『今度これやろう』が増えています。",
        message: "その城下町、毎週なにか始まってる。"
      },
      ISTJ: {
        name: "堅実石垣守備型",
        castle: "丸亀城、弘前城、松山城",
        description: "派手さよりも確実性。石垣のように積み上げることを大切にする、信頼感のある城主です。",
        strength: "継続力・責任感・安定感があり、守りを任せたら強いです。",
        weakness: "予定外の奇襲に対して、少し表情が固まります。",
        modern: "締切とルールを守るタイプ。地味に一番組織を支えています。",
        message: "あなたの石垣、ちゃんと強い。もっと誇っていい。"
      },
      ISFJ: {
        name: "民を守る内堀型",
        castle: "彦根城、犬山城、弘前城",
        description: "自分が目立つより、大切な人が安心できることを重視するタイプ。優しさがそのまま防御力になっています。",
        strength: "気配りができ、周囲を安心させる力があります。",
        weakness: "守る範囲を広げすぎて、自分の兵糧が減りがち。",
        modern: "みんなの様子をよく見ている人。無理してないかだけ注意。",
        message: "その内堀、優しいけどちゃんと深い。"
      },
      ESTJ: {
        name: "実務奉行統治型",
        castle: "名古屋城、江戸城、福山城",
        description: "理想よりも運営。城を維持し、人を動かし、仕組みで勝つタイプです。",
        strength: "管理・実行・改善が得意で、混乱した場を整えられます。",
        weakness: "効率化しすぎて、家臣の雑談スペースまで削りがち。",
        modern: "会議の目的と締切を確認してくれる人。組織に一人いると強いです。",
        message: "その城、ちゃんと回ってます。奉行が優秀。"
      },
      ESFJ: {
        name: "城下町世話役型",
        castle: "会津若松城、松江城、岡山城",
        description: "人のつながりを大切にする城主。民の表情や家臣の空気まで見ながら城を運営します。",
        strength: "周囲を支え、あたたかい共同体をつくる力があります。",
        weakness: "人のことを気にしすぎて、本丸の自分が後回しになりがち。",
        modern: "飲み会の席順や誕生日に強いタイプ。場の温度を上げられます。",
        message: "あなたの城下町、たぶん住民満足度が高い。"
      },
      ISTP: {
        name: "実戦忍び城型",
        castle: "上田城、忍城、岩櫃城",
        description: "多くを語らず、必要な時に動く実戦派。派手な理念より、目の前の状況を見て最適に動きます。",
        strength: "冷静な判断と対応力があり、現場で頼りになります。",
        weakness: "説明が短すぎて、家臣が『殿、もう少し共有を』となることがあります。",
        modern: "トラブル時に急に頼れる人。普段は静かでも実は見ています。",
        message: "その抜け道、いつ作ったんですか。"
      },
      ISFP: {
        name: "美意識小城型",
        castle: "犬山城、松本城、丸岡城",
        description: "大きさよりも空気感。自分が心地よいと思える美しさや余白を大切にします。",
        strength: "感性が鋭く、人の心に残る雰囲気をつくれます。",
        weakness: "言語化する前に『なんか違う』で判断しがち。",
        modern: "センスで場を整える人。静かだけど好き嫌いはかなりはっきりしています。",
        message: "その小城、派手じゃないのに忘れられない。"
      },
      ESTP: {
        name: "突撃攻城隊長型",
        castle: "熊本城、小田原城、上田城",
        description: "考えるよりまず動く、現場で強いタイプ。ピンチほどテンションが上がる城主です。",
        strength: "行動力と度胸があり、停滞した場を一気に動かせます。",
        weakness: "勢いで出陣して、あとから兵糧を確認することがあります。",
        modern: "イベント当日のトラブル対応に強い。ノリと突破力があります。",
        message: "その突撃力、頼もしい。でも地図は持って。"
      },
      ESFP: {
        name: "天下布武エンタメ型",
        castle: "安土城、大阪城、熊本城",
        description: "場を明るくし、人を楽しませる華のある城主。城は見られてこそ、語られてこそと思っています。",
        strength: "周囲を巻き込み、場の空気を一瞬で変える力があります。",
        weakness: "映えを優先して、維持費が後から追いかけてくることがあります。",
        modern: "人前に出ると強い。写真を撮られる側でも撮る側でも盛り上げます。",
        message: "その天守、ちょっと派手。でも嫌いじゃない。"
      }
    };

    form.addEventListener("submit", function(e) {
      e.preventDefault();

      const data = new FormData(form);
      const score = { E: 0, I: 0, S: 0, N: 0, T: 0, F: 0, J: 0, P: 0 };

      for (const value of data.values()) {
        if (score[value] !== undefined) score[value]++;
      }

      const type =
        (score.E >= score.I ? "E" : "I") +
        (score.N >= score.S ? "N" : "S") +
        (score.T >= score.F ? "T" : "F") +
        (score.J >= score.P ? "J" : "P");

      const r = results[type];

      document.getElementById("typeName").textContent = r.name;
      document.getElementById("typeCode").textContent = type + "｜城主タイプ";
      document.getElementById("description").textContent = r.description;
      document.getElementById("strength").textContent = r.strength;
      document.getElementById("weakness").textContent = r.weakness;
      document.getElementById("castle").textContent = r.castle;
      document.getElementById("modern").textContent = r.modern;
      document.getElementById("message").textContent = r.message;

      setBar("barIE", score.E, score.I);
      setBar("barSN", score.N, score.S);
      setBar("barTF", score.T, score.F);
      setBar("barJP", score.J, score.P);

      const favorite = document.getElementById("favoriteCastle").value || "未記入";
      const reason = document.getElementById("freeReason").value || "未記入";

      const prompt = `あなたは「戦国城性格診断AI」です。

以下の診断結果と自由回答をもとに、この人をさらに面白く深掘りしてください。

診断は断定しすぎず、「なんかわかる！」となるエンタメ性を重視してください。
少しユーモアを入れつつ、悪口にはしないでください。

【診断結果】
タイプコード：${type}
城主タイプ名：${r.name}
特徴：${r.description}
強み：${r.strength}
弱点：${r.weakness}
向いている城：${r.castle}
現代での生態：${r.modern}

【自由回答】
好きな城：${favorite}
理由：${reason}

【出力形式】
・さらに詳しい性格分析
・この人の城の構造
・家臣から見た印象
・攻める側から見た嫌なところ
・現代での人間関係
・最後に一言`;

      document.getElementById("claudePrompt").textContent = prompt;

      resultSection.style.display = "block";
      resultSection.scrollIntoView({ behavior: "smooth" });
    });

    function setBar(id, rightScore, leftScore) {
      const total = rightScore + leftScore;
      const percent = total === 0 ? 50 : Math.round((rightScore / total) * 100);
      document.getElementById(id).style.width = percent + "%";
    }

    copyBtn.addEventListener("click", async function() {
      const text = document.getElementById("claudePrompt").textContent;
      try {
        await navigator.clipboard.writeText(text);
        copyBtn.textContent = "コピーしました！Claudeに貼れます";
        setTimeout(() => copyBtn.textContent = "Claude用プロンプトをコピーする", 2200);
      } catch (err) {
        alert("コピーできませんでした。下の文章を手動でコピーしてください。");
      }
    });
  </script>
</body>
</html>
