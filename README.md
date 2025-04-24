const apiKey = 'YOUR_API_KEY_HERE';
const url = `https://newsdata.io/api/1/news?apikey=${apiKey}&q=forex&language=en`;

fetch(url)
    .then(response => response.json())
    .then(data => {
        const newsList = document.getElementById("news-list");
        newsList.innerHTML = ''; // Clear the placeholder

        data.results.slice(0, 5).forEach(news => {
            const li = document.createElement("li");
            li.innerHTML = `<a href="${news.link}" target="_blank">${news.title}</a>`;
            newsList.appendChild(li);
        });
    })
    .catch(error => {
        console.error("Error fetching news:", error);
    });
