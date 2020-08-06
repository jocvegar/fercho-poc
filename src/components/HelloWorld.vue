<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div id="product-compofnent-1596731849451f"></div>
  </div>
</template>

<script>

var scriptURL = 
"https://sdks.shopifycdn.com/buy-button/latest/buy-button-storefront.min.js";

if (window.ShopifyBuy) {
  if (window.ShopifyBuy.UI) {
    ShopifyBuyInit();
  } else {
    loadScript();
  }
} else {
  loadScript();
}
function loadScript() {
  var script = document.createElement('script');
  script.async = true;
  script.src = scriptURL;
  (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(script);
  script.onload = ShopifyBuyInit;
}
function ShopifyBuyInit() {
  var client = ShopifyBuy.buildClient({
    domain: 'otra-vez-hn.myshopify.com',
    storefrontAccessToken: '576d5f64e5cfecf689c26cce76d840c7',
  });
  ShopifyBuy.UI.onReady(client).then(function (ui) {
    ui.createComponent('product', {
      id: '5500411740325',
      node: document.getElementById('product-component-1596731849451'),
      moneyFormat: 'L%20%7B%7Bamount%7D%7D',
      options: {
        "product": {
          "styles": {
            "product": {
              "@media (min-width: 601px)": {
                "max-width": "calc(25% - 20px)",
                "margin-left": "20px",
                "margin-bottom": "50px"
              }
            },
            "button": {
              "border-radius": "12px"
            }
          },
          "text": {
            "button": "Agregar"
          }
        },
        "productSet": {
          "styles": {
            "products": {
              "@media (min-width: 601px)": {
                "margin-left": "-20px"
              }
            }
          }
        },
        "modalProduct": {
          "contents": {
            "img": false,
            "imgWithCarousel": true,
            "button": false,
            "buttonWithQuantity": true
          },
          "styles": {
            "product": {
              "@media (min-width: 601px)": {
                "max-width": "100%",
                "margin-left": "0px",
                "margin-bottom": "0px"
              }
            },
            "button": {
              "border-radius": "12px"
            }
          },
          "text": {
            "button": "Add to cart"
          }
        },
        "cart": {
          "styles": {
            "button": {
              "border-radius": "12px"
            }
          },
          "text": {
            "title": "Carrito",
            "total": "Subtotal",
            "empty": "Tu carrito esta vacio",
            "notice": "Confirmar dirreción",
            "button": "Comprar!",
            "noteDescription": "Instrucciones"
          },
          "contents": {
            "note": true
          }
        }
      },
    });
  });
}

export default {
  name: "HelloWorld",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h1 {
  margin: 40px 0 0; 
}
a {
  color: #42b983;
}
</style>
