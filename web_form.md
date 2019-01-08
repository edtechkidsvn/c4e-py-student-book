# C4E Student book
## Web form

1.  HTML Form
- Bọc thẻ `<form \>` vào các input cần được gửi nội dung đi

<pre>
<b>&lt;form method="POST"&gt;</b>
  &lt;input &gt;
  &lt;input &gt;
  ...
<b>&lt;/form&gt;</b>
</pre>

- Trong các thẻ `<input name="" \>`, cần có attribute __`"name"`__ để đánh nhãn cho nội dung của các thẻ này

<pre>
...
&lt;input <b>name="image"</b> &gt;
...
</pre>

2. Để thực hiện `POST`, cần điều chỉnh ở cả hai phía client và server như sau:
- **Client**: __`method="POST"`__ trong thẻ form

<pre>
&lt;form <b>method="POST"</b>&gt;
...
</pre>


- **Server**: Chấp nhận cả GET và POST trong router

<pre>
@app.route('/...', <b>methods=["GET", "POST"]</b>)
...
</pre>

3. Khi gặp lỗi `Bad request`, thường nguyên nhân là do `key` trong input và khi bóc tách form không giống nhau

<pre>
&lt;form method="POST"&gt;
  &lt;input <b>name="imag"</b>&gt;
&lt;/form&gt;
</pre>

<pre>
@app.route('/...', methods=["GET", "POST"])
...
form = rquest.form
image = form<b>["image"]</b>
</pre>
