---
title: Td Tag
localeTitle: اليوم الثاني
---
## تي دي تاج

تحدد العلامة `<td>` خلية قياسية في جدول HTML.

يحتوي جدول HTML على نوعين من الخلايا:

*   خلايا العنوان - تحتوي على معلومات رأس (تم إنشاؤها باستخدام العنصر `<th>` )
*   الخلايا القياسية - تحتوي على بيانات (تم إنشاؤها باستخدام عنصر `<td>` )

يكون النص الموجود في عناصر `<th>` غامقًا ومركّزًا بشكل افتراضي. النص في عناصر `<td>` منتظم ومحاذاة إلى اليسار بشكل افتراضي.

### مثال

```html
<html>
<head>
<title>Td Tag Example</title>
</head>
<body>
<table>
  <tr>
    <th>Header1</th>
    <th>Header2</th>
  </tr>
  <tr>
    <td>Cell A</td>
    <td>Cell B</td>
  </tr>
</table>
</body>
</html>
```