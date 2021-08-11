Write a content to the blob from an existing file 

```js
  blobStream.write(fs.readFileSync('./index.json', 'utf8', function (err, data) {

    return data

  }))

```

We can also write a content in a very simple way

```js
const blobStream = blob.createWriteStream();

blobStream.write(content)
```
