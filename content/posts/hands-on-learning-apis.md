---
title: "Hands-on Learning: APIs"
subtitle: "Why Python calls itself 'batteries included'"
date: 2021-09-13T16:04:48-10:00
draft: false
---
So last time, I compared Computer Science with Software Development. My dirt-under-the-fingernails viewpoint: make stuff, break stuff, learn by doing. I am excited for pushback from those of a more academic persuasion!

## Learn By Doing: Pick a Problem

I wanted a project to shake the rust off (not the [Rust](https://www.rust-lang.org/). That came later.)

So I asked my partner for a user story. As a firm administrator, she wanted to visualize the tax returns processed by her firm over time, so they could identify constraints and bottlenecks.

More exotic and exhilarating datasets, there certainly are. But this one had a user! I wanted a practical problem, not a theoretical one.

My approach went like this:

1. pick a problem

2. choose a small part of it

3. solve that part in a simple but interesting way

4. fix the dumb mistakes


I decided to throw all the fun tools at it! For that, I’d use my old pal: our trusty “batteries-included” language, Python. (For those who read the last page first, [here’s what I came up with](https://github.com/oatnog/tih-api-flask).)

## import \* from batteries

So what did I have, and what did I want to produce?

I had a workflow tracker with a whole lot of information. Supposedly, it could offer it up via its own API. But that cost extra, and the company didn’t seem to know exactly how to do it. (Acquisitions!)

So I could get at the data from an Excel spreadsheet, run as a report by hand. Ouch, but it gets one started. I had read spreadsheets into my Python programs before. But what new trick could I try this time?

[Pandas](https://pandas.pydata.org/)! The beloved data analysis tool. Way overkill for this data, perhaps, but I’d been itching for an excused to learn how to use it.

And I should store the data, rather than analyze and extract it over and over. Obvious choice: a relational database, say [sqlite](https://docs.python.org/3/library/sqlite3.html). Other choices--stick it in The Cloud, via [hosted mongodb](https://www.mongodb.com/cloud/atlas) or [Amazon’s SimpleDB](https://aws.amazon.com/simpledb/).

These were all very reasonable choices, but in the end I went really simple and staying in the Pandas ecosystem and chose… [Feather files!](https://arrow.apache.org/docs/python/feather.html) Didn’t see that coming, did you?

To do the “serving up API endpoints”, it was either [FastAPI](https://fastapi.tiangolo.com/) or [Flask](https://palletsprojects.com/p/flask/). I decided to learn FastAPI another time, and stick with what I knew. For once.

## Nice List. Now What?

I believe that learning happens all through the process, from sifting and selecting tools to trying them out to adapting and finishing. But yeah, get something done! “Real Artists Ship,” etc.

So here’s what got done:

Pandas is easy to use! The documentation helps point you through its many options to your particular need.

```python
for excel_file in spreadsheets.rglob('*.xlsx'):
    # depends on openpyxl
    app.logger.info(f"Importing {excel_file}")
    status_on_date = pd.read_excel(excel_file, usecols=['Current Status', 'Responsible Person', 'Tax Staff'])
```

Then using feather files (like Python’s “pickle” objects-saved-as-files) made saving and reading the data very simple.

And Flask is always a treat. Perfect for providing a URL fulla JSON.

```python
@app.route('/status/<isodate>', methods=['GET'])
def status(isodate):
    """List all tax filings, sorted by status """
    feather_filename = feather_path.joinpath(isodate)
    if feather_filename.exists():
        app.logger.info(f"Reading in {feather_filename}")
        status_on_date = pd.read_feather(feather_filename)
        status_counts = status_on_date.value_counts('Current Status')
        # we want the JSON in a particular process order. So match it to a look-up table.
        mystatus = {
            'filings': [{'status': tr_status, 'total': int(status_counts[tr_status])}
             for tr_status in TAX_RETURN_STATUS
             if tr_status in status_counts.keys()]}

        return jsonify(mystatus)
```

I could have used [Python for the charts](https://plotly.com/python/basic-charts/), too. But in the spirit of learning by doing, I decided to split this project into a front end and back end.

Later on, I’ll write about my front-end adventures with JavaScript and Vue. ( [I wrote a bit about it already elsewhere](https://goosemoon.org/posts/learning-javascript-ii/).)

## And What Have We Learned?

- It’s very easy to put data up into a JSON API with Flask. I’ll try FastAPI someday.

- Staying inside an ecosystem like pandas can help streamline work (feather).

- But once it’s done, refactoring to support more integrations sounds like fun!

- We don’t always do things the smartest and most scalable way when learning something new.

- But there’s something wonderful about a working prototype!


So, grab some tools and start making something!

