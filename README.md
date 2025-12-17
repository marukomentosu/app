<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>野球配球レコーダー</title>
    <style>
        body { font-family: sans-serif; text-align: center; background: #f0f4f8; }
        #strike-zone {
            display: grid;
            grid-template-columns: repeat(3, 80px);
            grid-template-rows: repeat(3, 80px);
            gap: 5px;
            justify-content: center;
            margin: 20px auto;
            background: #fff;
            padding: 10px;
            border: 3px solid #333;
        }
        .cell {
            width: 80px; height: 80px;
            border: 1px solid #ccc;
            display: flex; align-items: center;
            justify-content: center;
            cursor: pointer;
            background: #eef;
        }
        .cell:active { background: #abc; }
        .controls { margin-bottom: 20px; }
        button { padding: 10px 20px; font-size: 16px; margin: 5px; border-radius: 8px; border: none; background: #007bff; color: white; }
        #log { max-width: 400px; margin: 20px auto; text-align: left; background: #fff; padding: 10px; border-radius: 8px; }
    </style>
</head>
<body>

    <h2>配球入力レコーダー</h2>

    <div class="controls">
        <select id="pitch-type" style="font-size: 18px; padding: 5px;">
            <option value="ストレート">ストレート</option>
            <option value="スライダー">スライダー</option>
            <option value="カーブ">カーブ</option>
            <option value="フォーク">フォーク</option>
            <option value="チェンジアップ">チェンジアップ</option>
        </select>
    </div>

    <p>コースをタップして入力</p>
    <div id="strike-zone">
        <div class="cell" onclick="recordPitch('高め左')"></div>
        <div class="cell" onclick="recordPitch('高め中')"></div>
        <div class="cell" onclick="recordPitch('高め右')"></div>
        <div class="cell" onclick="recordPitch('真ん中左')"></div>
        <div class="cell" onclick="recordPitch('真ん中')"></div>
        <div class="cell" onclick="recordPitch('真ん中右')"></div>
        <div class="cell" onclick="recordPitch('低め左')"></div>
        <div class="cell" onclick="recordPitch('低め中')"></div>
        <div class="cell" onclick="recordPitch('低め右')"></div>
    </div>

    <div id="log">
        <strong>【投球履歴】</strong>
        <ul id="history"></ul>
    </div>

    <script>
        let pitchCount = 1;

        function recordPitch(course) {
            const pitchType = document.getElementById('pitch-type').value;
            const historyList = document.getElementById('history');
            
            // 新しい履歴の作成
            const listItem = document.createElement('li');
            listItem.textContent = `${pitchCount}球目: ${pitchType} (${course})`;
            
            // 履歴をリストの先頭に追加
            historyList.insertBefore(listItem, historyList.firstChild);
            
            pitchCount++;
        }
    </script>
</body>
</html>
