---
cssclasses: cards, cards-cover, cards-2-3, table-max
---
```dataview
table without id ("![](" + poster + ")") as Poster, file.link as Title, year as Year, director as Director, "⭐ " + scoreImdb as "⭐ IMDB", rating, genre from "uni/03-Resources/Movies" where contains(status, "complete")
```
