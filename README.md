# vue-chart

This is a [Example Demo](//miaolz123.github.io/vue-chart/) of vue-chart

```html
<!DOCTYPE html>
<html>

<head>
  <title>vue-chart</title>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
</head>

<body>
  <vue-chart type="doughnut" :data="data"></vue-chart>
  <br>
  <p style="text-align:center">
    REMAIN: {{ data.datasets[0].data[0] }}, LEAVE: {{ data.datasets[0].data[1] }}
    & Powered by <a href="//github.com/miaolz123/vue-chart" target="_blank">VueChart</a>
  </p>
  <script src="dist/vue.js"></script>
  <script src="dist/vue-chart.js"></script>
  <script>
    Vue.use(VueChart);
    var vm = new Vue({
      el: "body",
      data: {
        data: {
          labels: ["REMAIN", "LEAVE"],
          datasets: [{
            backgroundColor: ["#36A2EB", "#FF6384"],
            data: [1, 1]
          }]
        }
      },
      ready() {
        var root = this;
        var refresh = function() {
          var data = root.data.datasets[0].data;
          var vote = Math.floor(Math.random() * 10);
          data[vote % 2] += vote;
          root.data = {
            datasets: [{ data: data }],
          };
        };
        setInterval(refresh, 3000);
      },
    });
  </script>
</body>

</html>
```

# License

Copyright (c) 2016 [miaolz123](https://github.com/miaolz123) by [MIT](https://opensource.org/licenses/MIT)