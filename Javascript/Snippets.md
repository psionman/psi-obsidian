tage: #date-format-js
## Date format

```javascript 
function formatDate(event_date) {
const eventDate = new Date(event_date);

const formatted = eventDate.toLocaleDateString('en-GB', {
	day: '2-digit',
	month: 'short',
	year: 'numeric',
	hour: '2-digit',
	minute: '2-digit',
	hour12: false
}).replace(',', ' at');

return formatted;
}
```

Input is
```
2026-01-01T15:28:25.059000Z
```
(returned as datetime form Django, but interpteted as a string in js see [[Django/Snippets#Output dates for js]]

output
```
01 Jan 2026 at 15:28
```