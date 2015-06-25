## LiveJournal XMLRPC for Node

`npm install livejournal`

## XMLRPC

* http://wh.lj.ru/s2/developers/f/LiveJournal_XML-RPC_Specification_(EN).pdf
* http://www.livejournal.com/doc/server/ljp.csp.xml-rpc.protocol.html

Examples

```javascript
LiveJournal.RPC.getevents({
  journal: 'brad',
  auth_method: 'noauth',
  selecttype: 'lastn',
  howmany: 20
}, function(err, value) {
  console.log(value.events);
});
```

```javascript
LiveJournal.RPC.getevents({
  journal: 'brad',
  auth_method: 'noauth',
  selecttype: 'one',
  ditemid: '29215'
}, function(err, post) {
  console.log(post.events[0]);
});
```

## JSONRPC

There is no public description of LiveJournal JSON RPC methods, but you can check `Site.rpc.public` on `http://livejournal.com`. Because the data is stored on CDN, you can access the data from anywhere.

Those are current ones:
```
discovery.author_posts
comment.get_thread
latest.get_entries
browse.get_posts
gifts.get_gifts_categories
gifts.get_all_gifts
homepage.get_categories
discovery.suggest
sitemessage.get_message
discovery.get_categories
browse.get_categories
writers_block.get_list
discovery.today
discovery.get_feed
discovery.get_item
homepage.get_rating
browse.get_communities
```

Examples

```js
LiveJournal.jsonRPC.request('latest.get_entries', {
  first_timepost: 1435262400
}, function(err, res) {
  console.log(res.body.result.params.recent);
});
```

You can access method list using `LiveJournal.jsonRPC.methods`.

## Other

* http://www.livejournal.com/developer/
* http://lj-dev.livejournal.com/

## Tests

```
npm install jasmine-node -g
jasmine-node spec/
```
