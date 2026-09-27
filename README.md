# gulabu
-----------
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>WebFinder</title>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: #f4f6f8;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .container {
            width: 90%;
            max-width: 700px;
            text-align: center;
        }

        h1 {
            font-size: 48px;
            margin-bottom: 10px;
            color: #222;
        }

        p {
            color: #666;
            margin-bottom: 30px;
        }

        .search-box {
            display: flex;
            background: white;
            border-radius: 40px;
            padding: 8px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.12);
        }

        input {
            flex: 1;
            border: none;
            outline: none;
            font-size: 18px;
            padding: 15px 20px;
            border-radius: 40px;
        }

        button {
            border: none;
            background: #2563eb;
            color: white;
            padding: 0 28px;
            border-radius: 35px;
            font-size: 16px;
            cursor: pointer;
        }

        button:hover {
            background: #1d4ed8;
        }

        .engines {
            margin-top: 20px;
        }

        select {
            padding: 10px 15px;
            border-radius: 8px;
            border: 1px solid #ccc;
            font-size: 15px;
        }

        @media (max-width: 500px) {
            h1 {
                font-size: 38px;
            }

            .search-box {
                padding: 5px;
            }

            input {
                width: 50%;
                font-size: 15px;
            }

            button {
                padding: 0 18px;
            }
        }
    </style>
</head>

<body>

    <div class="container">

        <h1>WebFinder</h1>

        <p>Search the internet using a keyword</p>

        <div class="search-box">

            <input
                type="text"
                id="searchInput"
                placeholder="Enter a keyword..."
            >

            <button onclick="searchInternet()">
                Search
            </button>

        </div>

        <div class="engines">

            <select id="searchEngine">
                <option value="google">Google</option>
                <option value="bing">Bing</option>
                <option value="duckduckgo">DuckDuckGo</option>
            </select>

        </div>

    </div>

    <script>

        function searchInternet() {

            const keyword =
                document.getElementById("searchInput").value.trim();

            const engine =
                document.getElementById("searchEngine").value;

            if (keyword === "") {
                alert("Please enter a keyword.");
                return;
            }

            const encodedKeyword =
                encodeURIComponent(keyword);

            let url;

            if (engine === "google") {

                url =
                    "https://www.google.com/search?q="
                    + encodedKeyword;

            } else if (engine === "bing") {

                url =
                    "https://www.bing.com/search?q="
                    + encodedKeyword;

            } else {

                url =
                    "https://duckduckgo.com/?q="
                    + encodedKeyword;

            }

            window.location.href = url;
        }

        // Press Enter to search
        document
            .getElementById("searchInput")
            .addEventListener("keydown", function(event) {

                if (event.key === "Enter") {
                    searchInternet();
                }

            });

    </script>

</body>
</html>