# 找　mssql (sql srever) tabel schema 

> link: `https://medium.com/@duffn/getting-started-with-loopback-and-sql-server-653aeb404cbb`



~~~js 
var app = require('./server');
var dataSource = app.dataSources.msSQL;

dataSource.discoverSchema('members', {
  owner: 'dbo'
}, function(error, schema) {
  console.log(JSON.stringify(schema, null, ' '));
});


~~~