# Moed Shabbat times widget and API

A small embeddable widget and a free JSON API for Shabbat times, zmanim and Jewish holidays, served by [moedcal.com](https://moedcal.com/). No key, no account, no cookie.

Useful for synagogue and community websites that publish their times as a PDF or by hand.

## Widget

Paste this into a page. The first part of the path is the language (`en`, `fr` or `he`), the second is the city.

```html
<iframe src="https://moedcal.com/widget-frame/en/new-york/"
        title="Shabbat times" width="360" height="190"
        style="border:0;max-width:100%" loading="lazy"></iframe>
```

It shows the next Friday, the Torah portion, candle lighting and Havdalah, follows the visitor's light or dark setting, and is right to left in Hebrew. A working page is in [`examples/embed.html`](examples/embed.html). City addresses are the ones used on the site: `paris`, `marseille`, `london`, `new-york`, `jerusalem`.

You can pick a city and copy the code on the [widget page](https://moedcal.com/en/widget/).

## API

Read only. Please stay under one request per second and cache responses for an hour.

| Request | Returns |
|---|---|
| [`/api/v1/shabbat/?city=new-york`](https://moedcal.com/api/v1/shabbat/?city=new-york) | Next Shabbat: candle lighting, Havdalah, Rabbeinu Tam, Torah portion, haftarah. Optional `date=YYYY-MM-DD`. |
| [`/api/v1/zmanim/?city=new-york&date=2026-11-13`](https://moedcal.com/api/v1/zmanim/?city=new-york&date=2026-11-13) | The zmanim of a day, each with its rounding direction. |
| [`/api/ical/fetes/?year=2027&lang=en`](https://moedcal.com/api/ical/fetes/?year=2027&lang=en) | Holidays and fasts of a year as an `.ics` file. |

```bash
curl "https://moedcal.com/api/v1/shabbat/?city=new-york"
```

The calculation method is described on [moedcal.com](https://moedcal.com/en/widget/).

## Licence

The code in this repository (the embed snippet and example) is under the [MIT licence](LICENSE).

The data returned by the API is under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/): credit "Times: Moed" with a link to moedcal.com. The widget carries that link, and it must stay in place.

Times are calculated. For a halakhic decision, follow your rabbi and your community's custom.
