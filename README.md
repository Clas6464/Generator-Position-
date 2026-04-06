# Generator-Position-
JS/HTML/CSS code designed to generate positions for fact-checking purposes.

function onOpen() {
  const ui = SpreadsheetApp.getUi();
  ui.createMenu('🤖 Generator Pozic')
      .addItem('Generator Pozic', 'showSidebar')
      .addToUi();
}

function showSidebar() {
  const html = `
    <style>
      body { font-family: 'Segoe UI', sans-serif; padding: 15px; background-color: #f4f7f6; color: #b5b3b3; }
      .input-group { margin-bottom: 12px; }
      label { font-weight: 600; display: block; margin-bottom: 5px; font-size: 13px; color: #b5b3b3; }
      input { width: 100%; padding: 10px; border: 1px solid #ddd; border-radius: 6px; box-sizing: border-box; outline: none; }
      input:focus { border-color: #1a73e8; box-shadow: 0 0 3px rgba(26,115,232,0.3); }
      button { width: 100%; padding: 12px; background: #1a73e8; color: white; border: none; border-radius: 6px; cursor: pointer; font-size: 15px; font-weight: bold; margin-top: 10px; transition: background 0.2s; }
      button:hover { background: #1557b0; }
      #result { margin-top: 20px; padding: 12px; background: #fff; border: 1px solid #e0e0e0; border-radius: 6px; max-height: 250px; overflow-y: auto; font-family: 'Courier New', monospace; font-size: 13px; line-height: 1.5; }
      .block-sep { color: #1a73e8; border-bottom: 1px dashed #ccc; margin: 10px 0; font-weight: bold; }
      body { 

    font-family: 'Segoe UI', sans-serif; 

    padding: 15px; 

    color: #333;

    

    background-image: url('https://preview.redd.it/i-made-some-phone-wallpapers-from-the-first-4-episodes-v0-xoh71m011woc1.png?width=640&crop=smart&auto=webp&s=b68d76ef341b8d1bba806266c59a953751f21918'); 

    background-size: cover; 

    background-position: center;

    background-attachment: fixed;

  }



  

  .container {

    background: rgba(255, 255, 255, 0.85); 

    padding: 15px;

    border-radius: 10px;

    box-shadow: 0 4px 6px rgba(0,0,0,0.1);

  }



  .input-group { margin-bottom: 12px; }

  label { font-weight: 600; display: block; margin-bottom: 5px; font-size: 13px; color: #b5b3b3; }

  input { width: 100%; padding: 10px; border: 1px solid #ddd; border-radius: 6px; box-sizing: border-box; }

  

  button { 

    width: 100%; padding: 12px; background: #90EE90; color: white; border: none; 

    border-radius: 6px; cursor: pointer; font-size: 15px; font-weight: bold; margin-top: 10px; 

  }

  

  #result { 

    margin-top: 20px; padding: 12px; background: rgba(255, 255, 255, 0.9); 

    border: 1px solid #e0e0e0; border-radius: 6px; max-height: 200px; overflow-y: auto; 

    font-family: monospace; 

  }

  .block-sep { color: #1a73e8; border-bottom: 1px dashed #ccc; margin: 10px 0; font-weight: bold; }
    </style>
    
  

    <div class="input-group">
      <label>Sektor + Litera</label>
      <div style="display: flex; gap: 5px;">
        <input type="text" id="num1" placeholder="8" style="flex: 2;">
        <input type="text" id="let" placeholder="H" style="flex: 1;">
      </div>
    </div>

    <div class="input-group">
      <label> Kolik pater (5 nebo 8) </label>
      <input  id="midMax" value="5">
    </div>

    <div class="input-group">
      <label>Od kterého čísla začínáš?</label>
      <input  id="num2" value="1">
    </div>

    <div class="input-group">
      <label>Max čísel </label>
      <input  id="countN" value="2">
    </div>

    <button onclick="generate()">Create</button>

    <div id="result">Ty vole . . . </div>

    <script>
      function generate() {
        const n1 = document.getElementById('num1').value;
        const l = document.getElementById('let').value;
        const midMax = parseInt(document.getElementById('midMax').value);
        const startN2 = parseInt(document.getElementById('num2').value);
        const repeatN = parseInt(document.getElementById('countN').value);
        
        let htmlRes = "";
        
        if (!n1 || !l || isNaN(midMax)) {
          document.getElementById('result').innerText = "Ty vole, ne maš napsáno správně ";
          return;
        }

        for (let j = 0; j < repeatN; j++) {
          let currentLastNum = startN2 + j;
          
          for (let i = 1; i <= midMax; i++) {
            htmlRes += n1 + l + "-" + i + "-" + currentLastNum + "<br>";
          }
          
          
        }
        
        document.getElementById('result').innerHTML = htmlRes;
      }
    </script>
  `;
  const userInterface = HtmlService.createHtmlOutput(html)
      .setTitle('Generator Pozic')
      .setWidth(320);
  SpreadsheetApp.getUi().showSidebar(userInterface);
}
