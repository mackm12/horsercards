<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>College Football Scores Ticker</title>
    <style>
        #ticker-container {
            width: 100%;
            overflow: hidden;
            background-color: #013369; /* NCAA blue */
            color: white;
            padding: 10px 0;
            font-family: Arial, sans-serif;
        }
        #ticker {
            white-space: nowrap;
            display: inline-block;
            padding-left: 100%;
            animation: ticker 30s linear infinite;
        }
        #ticker span {
            margin-right: 50px;
        }
        @keyframes ticker {
            0% { transform: translate3d(0, 0, 0); }
            100% { transform: translate3d(-100%, 0, 0); }
        }
    </style>
</head>
<body>
    <div id="ticker-container">
        <div id="ticker"></div>
    </div>

    <script>
        const CFB_BASE_URL = "https://site.api.espn.com/apis/site/v2/sports/football/college-football/scoreboard";
        
        // Add your tracked team IDs here
        const TRACKED_TEAMS = [
            "158, 135, 87, 2294, 356, 66"  // Example: Nebraska Cornhuskers
            // Add more team IDs as needed
        ];

        function getCfbUrl() {
            const today = new Date().toISOString().split('T')[0].replace(/-/g, '');
            return `${CFB_BASE_URL}?dates=${today}`;
        }

        async function fetchScores(url) {
            try {
                const response = await fetch(url);
                if (!response.ok) {
                    throw new Error(`HTTP error! status: ${response.status}`);
                }
                const data = await response.json();
                return data.events || [];
            } catch (e) {
                console.error("Error fetching scores:", e);
                return [];
            }
        }

        function getGameStatus(game) {
            const status = game.status.type.state;
            if (status === 'pre') {
                return `Scheduled: ${game.status.type.shortDetail}`;
            } else if (status === 'in') {
                return game.status.type.shortDetail;
            } else if (status === 'post') {
                return "Final";
            }
            return "Unknown";
        }

        function formatScores(games) {
            return games.filter(game => {
                const homeTeam = game.competitions[0].competitors.find(team => team.homeAway === 'home');
                const awayTeam = game.competitions[0].competitors.find(team => team.homeAway === 'away');
                return TRACKED_TEAMS.includes(homeTeam.team.id) || TRACKED_TEAMS.includes(awayTeam.team.id);
            }).map(game => {
                const homeTeam = game.competitions[0].competitors.find(team => team.homeAway === 'home');
                const awayTeam = game.competitions[0].competitors.find(team => team.homeAway === 'away');
                const gameStatus = getGameStatus(game);
                
                return `${awayTeam.team.abbreviation} ${awayTeam.score} @ ${homeTeam.team.abbreviation} ${homeTeam.score} - ${gameStatus}`;
            });
        }

        async function updateTicker() {
            const ticker = document.getElementById('ticker');
            try {
                const games = await fetchScores(getCfbUrl());
                const scores = formatScores(games);
                if (scores.length > 0) {
                    ticker.innerHTML = scores.map(score => `<span>${score}</span>`).join('');
                } else {
                    ticker.innerHTML = '<span>No games currently scheduled for tracked teams.</span>';
                }
            } catch (e) {
                console.error("Error updating ticker:", e);
                ticker.innerHTML = '<span>Unable to fetch scores. Retrying...</span>';
            }
        }

        // Initial update
        updateTicker();

        // Update every 60 seconds
        setInterval(updateTicker, 60000);
    </script>
</body>
</html>
