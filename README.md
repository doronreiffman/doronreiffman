AI and backend engineer in Jerusalem. I build AI tools and the data systems under them, mostly in Python and TypeScript on AWS.

### Live projects

Two sites built on Israeli public data that its source does not keep. Each project collects the data on AWS every day, stores every file write-once, and turns the history into an answer to one plain question.

<table>
<tr>
<td width="50%" valign="top">
<a href="https://dt4564wsgvijr.cloudfront.net"><img src="https://raw.githubusercontent.com/doronreiffman/flights-archive/main/docs/img/timeline.png" width="100%" alt="The Will It Fly? page for BZ 317 from Vienna: chance it's cancelled about 4%, chance it's delayed an hour or more about 17%, worked out mostly from the airline's history, then the flight's days as a strip."></a>
<br><sub>One flight's page on the live site.</sub>

**[Will It Fly?](https://dt4564wsgvijr.cloudfront.net)** · Tel Aviv airport

The chance a flight is cancelled, or delayed an hour or more, for every flight number. The airport's live board overwrites itself every 15 minutes, so the collector checks it every 2 minutes and keeps every version.

[Live site](https://dt4564wsgvijr.cloudfront.net) · [Code](https://github.com/doronreiffman/flights-archive)

</td>
<td width="50%" valign="top">
<a href="https://d153udx05irk2f.cloudfront.net"><img src="https://raw.githubusercontent.com/doronreiffman/il-grocery-prices/main/docs/img/deal-page-light.png" width="100%" alt="A product page: at Osher Ad, DEAL, 1.10 shekels off, usually 5.00, today 3.90, over a step chart of the price paid each day for 90 days, and the same product's deal at six other store formats."></a>
<br><sub>A product page, shown on sample data.</sub>

**[Deal or No Deal?](https://d153udx05irk2f.cloudfront.net)** · Israeli supermarkets

Checks today's promotion against what the product usually costs at that store, sales included, from the price files five chains must publish by law. Every morning it reads about 5 million price rows and rebuilds about 25,000 pages.

[Live site](https://d153udx05irk2f.cloudfront.net) · [Code](https://github.com/doronreiffman/il-grocery-prices)

</td>
</tr>
</table>

### How they're built

- **Nothing collected is ever overwritten.** Every file is written once and locked for 10 years (S3 Object Lock). The tables and pages are built from it, so a fix can rebuild them.
- **Polite collectors that stop cold.** Each identifies itself on every request, and at any sign of being blocked it stops and waits for a person instead of working around it.
- **Tests that are themselves tested.** Over 4,300 tests between the two projects, plus over 3,300 deliberately planted bugs that a script proves the tests catch (mutation testing), run in GitHub Actions.
- **Claims no stronger than the evidence.** A cancellation time is always a range, a chance reads "about" or "under", never "0%", and a price is "listed", never "you'll pay". A check before every upload refuses a page that breaks these rules.
- **Cheap, boring infrastructure.** Lambda, EventBridge Scheduler, S3 and CloudFront, with DuckDB over Parquet for the analysis. Both projects together run for a few dollars a month.

### AI projects

- **[Job Scout](https://github.com/doronreiffman/job-scout)**: a daily AI job-search assistant. It reads company careers feeds, LinkedIn alert emails and WhatsApp job groups, screens out what can't fit, scores the rest against your resume with Claude, and emails one digest. Python, Claude API, SQLite.
- **[Bitext support-data agent](https://github.com/doronreiffman/support-data-agent)** (2026): a LangGraph agent that analyses a public customer-support dataset through tool calls, with session memory and a Streamlit UI. An assignment from my Nebius Academy course.
- **[Moodika](https://github.com/doronreiffman/Moodika)** (2022): recommends a Spotify playlist from a free-text mood, using sentence-transformer embeddings and XGBoost. ITC Data Science Fellows final project, a team of three.

Open to AI engineering roles · [LinkedIn](https://www.linkedin.com/in/doronreiffman)
