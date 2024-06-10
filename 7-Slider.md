

Slider: 
```liquid
<link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/slick-carousel/1.9.0/slick.min.css"
  integrity="sha512-yHknP1/AwR+yx26cB1y0cjvQUMvEa2PFzt1c9LlS4pRQ5NOTZFWbhBig+X9G9eYW/8m0/4OXNx8pxJ6z57x0dw=="
  crossorigin="anonymous"
  referrerpolicy="no-referrer"
>
<link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/slick-carousel/1.9.0/slick-theme.min.css"
  integrity="sha512-17EgCFERpgZKcm0j0fEq1YCJuyAWdz9KUtv1EjVuaOz8pDnh/0nZxmU6BBXwaaxqoi9PQXnRWqlcDB027hgv9A=="
  crossorigin="anonymous"
  referrerpolicy="no-referrer"
>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css" crossorigin>
<script src="https://cdn.jsdelivr.net/npm/slick-carousel@1.8.1/slick/slick.min.js" defer="defer"></script>
<style>
    .slider-section {
        padding-bottom: 115px;
    }

  .testimonial-img {
  	display: flex;
  	gap: 20px;
  	justify-content: space-between;
  }
  .image-1-area {
  	display: flex;
  	align-items: center;
  	gap: 20px;
  }
  .client_content p {
	margin: 0;
}
  .image-2-area {
    display: black;
  }
    .card-one {
        border-radius: 8px;
        border: 0.554px solid #BABABA;
        background: rgba(0, 0, 0, 0.40);
        backdrop-filter: blur(8px);
        padding: 30px 30px 0px 30px;
    }
    .testimonial-img {
        display: flex;
        gap: 20px;
    }
    .testimonial-img p {
        color: #FFFFFF;
    }
    .quation {
    	width: 101px;
    	height: 92px;
    	object-fit: fill;
    }
      .testimonial-content{
        margin-top: 10px;
    }
    .testimonial-content p {
        color: #FFFFFF;
    }
    .slick-slider .prev_arrow:hover,
    .slick-slider .prev_arrow:active,
    .slick-slider .prev_arrow:focus{
        background:#06E500;
        color: #222;
        transition: all ease-in 0.8s;
    }

    .slick-slider .next_arrow:hover,
    .slick-slider .next_arrow:active,
    .slick-slider .next_arrow:focus{
        background:#06E500;
        color: #222;
        transition: all ease-in 0.8s;
    }
    .slick-slider .prev_arrow {
        background: #696969;
        width: 35px;
        height: 35px;
        color: #06E500;
        font-size: 20px;
        border-radius: 100%;
        display: inline-block;
        position: absolute;
        top: 110%;
        left: 47.4%;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        z-index: 9;
        border: 1px solid #06E5001F;
    }

    .slick-slider .next_arrow {
        background: #696969;
        width: 35px;
        height: 35px;
        color: #06E500;
        font-size: 20px;
        border-radius: 100%;
        display: inline-block;
        position: absolute;
        top: 110%;
        right: 47.5%;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        z-index: 9;
    }
    .slick-list{
      display: flex;
    }
    .slick-track {
  	display: flex;
  	gap: 8px;
  }
    @media screen and (min-width: 320px) {
      .image-2-area {
        display: none;
      }
      .slick-slider .prev_arrow {
        left: 39%;
      }
      .slick-slider .next_arrow {
        right: 39%
      }
    }
   @media screen and (min-width: 990px) {
     .image-2-area {
        display: block;
      }
       .slick-slider .prev_arrow {
        left:  47.4%;
      }
      .slick-slider .next_arrow {
        right:  47.4%;
      }
   }
</style>
<section class="slider-section">
  <div class="page-width">
    <div class="testimonial" id="test">
      {% for block in section.blocks %}
        <div class="card-one">
          <div class="testimonial-img">
            <div class="image-1-area">
              <div class="client__img">
              <img class="client" src="{{ block.settings.image-1 | image_url }}">
              </div>
              <div class="client_content">
                <p>{{ block.settings.title }}</p>
                <p>{{ block.settings.sub_title }}</p>
              </div>
            </div>
            <div class="image-2-area">
              <img class="quation" src="{{ block.settings.image-3 | image_url }}" alt="">
            </div>
          </div>
          <div class="testimonial-content">
            <img src="{{  block.settings.image-2 | image_url }}">
            <p>{{ block.settings.desc }}</p>
          </div>
        </div>
      {% endfor %}
    </div>
  </div>
</section>

<script>
  $(document).ready(function(){
      $('.testimonial').slick({
        infinite: true,
        slidesToShow: 3,
        slidesToScroll: 1,
        speed: 300,
        prevArrow: '<span class="prev_arrow"><i class="fa-solid fa-angle-left"></i></span>',
        nextArrow: '<span class="next_arrow"><i class="fa-solid fa-angle-right"></i></span>',
        autoplaySpeed: 2000,
          responsive: [
              {
                  breakpoint: 1024,
                  settings: {
                      slidesToShow: 3,
                      slidesToScroll: 1,
                      infinite: true,
                     
                  }
              },
              {
                  breakpoint: 766,
                  settings: {
                      slidesToShow: 2,
                      slidesToScroll: 1
                  }
              },
              {
                  breakpoint: 480,
                  settings: {
                      slidesToShow: 1,
                      slidesToScroll: 1
                  }
              }
          ]
      });
  });
</script>
{% schema %}
{
  "name": "Review Slider",
  "settings": [],
  "blocks": [
    {
      "type": "blog-banner",
      "name": "Blog Contant",
      "limit": 6,
      "settings": [
        {
          "type": "text",
          "id": "title",
          "label": "Title",
          "default": "input your title"

        },
        {
          "type": "text",
          "id": "sub_title",
          "label": "Sub Title",
          "default": "input your title"

        },
        {
          "type": "image_picker",
          "id": "image-1",
          "label": "photo 1"
        },
         {
          "type": "image_picker",
          "id": "image-2",
          "label": "photo 2"
        },
        {
          "type": "image_picker",
          "id": "image-3",
          "label": "Review 2"
        },
        {
          "type": "richtext",
          "id": "desc",
          "label": "Input you content",
          "default": "<p>input your content</p>"
        }
      ]
    }
  ],
  "presets": [
    {
      "name": "Review Slider"
    }
  ]
}
{% endschema %}

```