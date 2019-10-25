---
title: "QR Code Generator"
date: 2019-10-25T17:35:20+08:00
categories:
  - "Miscellaneous"
tags:
  - "QR"
---

I just use [qrious.js](https://github.com/neocotic/qrious) to implement a simple QR code generator.Please feel free to try online QR code generator to make your own QR codes. It supports four levels of error correction, you can choose the right size for your QR codes in the range of 100 to 1000 and click on a color swatch in the swatches panel to change the foreground and backgroud color.
    <style>
        main section {
            min-width: 250px;
            max-width: 50%;
            height: 100%;
            text-align: center;
        }
        main img {
            box-shadow: 0 0 10px 5px #666;
        }
        main form {
            padding: 25px 0 50px 0;
            text-align: left;
        }
        main textarea {
            display: flex;
            justify-content: center;
            align-items: center;
        }
        main form label {
            display: block;
            margin-top: 10px;
            color: #444;
            font-weight: bold;
        }
        main form input,
        main form select {
            margin: 0 auto; 
            width: 100%;
        }
        main form input:invalid {
            outline: 2px solid #f00;
            color: #f00;
        }
    </style>
        <img id="qrious">

        <form autocomplete="off">
            <label>
                value
                <textarea type="text" name="value" spellcheck="false" class="form-control" style="width:100%; height:150px;">Input your url</textarea>
            </label>

            <label>
                size
                <input type="number" name="size" placeholder="100" min="100" max="1000" value="250">
            </label>

            <label>
                level
                <select name="level">
                    <option value="L">L - 7% damage</option>
                    <option value="M">M - 15% damage</option>
                    <option value="Q">Q - 25% damage</option>
                    <option value="H">H - 30% damage</option>
                </select>
            </label>

            <label>
                background
                <input type="color" name="background" value="#ffffff">
            </label>

            <label>
                foreground
                <input type="color" name="foreground" value="#000000">
            </label>
        </form>
