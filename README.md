# Free Seo-Section for Shopify all themes


## How to set up the section

1. Create a new section in your theme editor
2. Copy the code inside the new section

## Code Snippet


{%- style -%}
  
  .seo-section * { margin:0; padding:0; box-sizing:border-box;}
  .seo-section .page-width { max-width: var(--page-width);
    margin: 0 auto; width:100%; }
  .seo-section h1, .seo-section h2, .seo-section h3, .seo-section h4, .seo-section h5, .seo-section h6 { font-weight:600; line-height:normal; }
  .seo-section a {text-decoration: none; color:{{ section.settings.link_color }}; }
  .seo-section h1, .seo-section .h1{ font-size: 42px; }
  .seo-section h2, .seo-section .h2{ font-size: 38px; }
  .seo-section h3, .seo-section .h3{ font-size: 34px; }
  .seo-section h4, .seo-section .h4{ font-size: 30px; }
  .seo-section h5, .seo-section .h5{ font-size: 28px; }
  .seo-section h6, .seo-section .h6{ font-size: 24px; }

  .full-width_heading h2 { margin-bottom: 25px;}
  .seo-section P, .seo-section ul { font-size:inherit }
  .seo-section P:last-child {margin-bottom: 0;}
  .seo-section P { margin-bottom: 15px;}
  .seo-section {line-height: normal;font-weight: 500; }
  .two-cloumn-section {display: flex;flex-flow: wrap;margin: 0 -15px;}  
  .left-block_row {width: 50%; padding: 0 15px;}  
  .right-block_row {width: 50%;padding: 0 15px;}  
  .full-width_row { margin-bottom: 35px;}  
  .inr-heading { margin-bottom: 10px;}  
  .content-block_cover { margin-bottom: 30px;}
  .seo-section ul li, .seo-section ol li {list-style: none; position: relative;padding-left: 22px;margin-bottom: 2px;}  
  .seo-section ul li:before, .seo-section ol li:before { content: "✓"; position: absolute;width: 14px;height: 14px;top: 4px;left: 0; }
  
  .section-{{ section.id }}-padding {
    padding-top: {{ section.settings.padding_top | times: 0.75 | round: 0 }}px;
    padding-bottom: {{ section.settings.padding_bottom | times: 0.75 | round: 0 }}px;
  }
  
  @media screen and (min-width: 750px) {
    .section-{{ section.id }}-padding {
      padding-top: {{ section.settings.padding_top }}px;
      padding-bottom: {{ section.settings.padding_bottom }}px;
    }
    .seo-section .page-width {
      padding: 0 1rem;
    }
  }
  @media screen and (max-width: 749px) {
     .seo-section .page-width {padding: 0 1rem; }
    .left-block_row {width: 100%;}    
    .right-block_row {width: 100%;}    
    .seo-section P { margin-bottom: 8px; }    
    .full-width_heading h2 {margin-bottom: 15px;}    
    .content-block_cover {margin-bottom: 20px;}
    .full-width_row { margin-bottom: 20px;}
  }

  
  {%- for block in section.blocks -%}
    {% case block.type %}
      
        {%- when 'fullwidthblock' -%}
          .seo-section .full-width_text {
            font-size: {{ block.settings.full_desktop_description_size }}px;
          }
          .seo-section .full-width_heading h2 {color:{{ block.settings.full_width_heading_color }}; }
          .seo-section .full-width_text {color:{{ block.settings.full_width_description_color }}; }
          @media screen and (max-width: 749px) {
            .seo-section .full-width_text {
              font-size: {{ block.settings.full_mobile_description_size }}px;
            }
        }
  
        {%- when 'leftblock' -%}
          .seo-section .left-block_row .inr-description {
            font-size: {{ block.settings.left_desktop_description_size }}px;
          }
          .seo-section .block-{{ block.id }} .inr-heading h3 { color:{{ block.settings.left_block_heading_color }}; }
          .seo-section .block-{{ block.id }} .inr-description { color:{{ block.settings.left_block_description_color }}; }
          @media screen and (max-width: 749px) {
            .seo-section .left-block_row .inr-description {
              font-size: {{ block.settings.left_mobile_description_size }}px;
            }
          }    
  
          {%- when 'rightblock' -%}   
          .seo-section .block-{{ block.id }} .inr-heading h3 { color:{{ block.settings.right_block_heading_color }}; }
          .seo-section .block-{{ block.id }} .inr-description { color:{{ block.settings.right_block_description_color }}; }
          .seo-section .right-block_row .inr-description {
            font-size: {{ block.settings.right_desktop_description_size }}px;
          } 
  
          @media screen and (max-width: 749px) {
            .seo-section .right-block_row .inr-description {
              font-size: {{ block.settings.right_mobile_description_size }}px;
            }
          }
  
    {%- endcase -%}
  {% endfor %}
  
{%- endstyle -%}


<div class="section-{{ section.id }}-padding" style="--page-width: {{ section.settings.page_width }}px">
  <div class="{% if section.settings.full_width %}page-width{% endif %}">
    
    <div class="main-block_cover">
      
        {%- for block in section.blocks -%}
          {% case block.type %}
            {%- when 'fullwidthblock' -%}
              <div class="full-width_row">
                <div class="full-width_cover block-{{ block.id }}" {{ block.shopify_attributes }}>
                  {% if block.settings.full_width_heading !=blank %}
                    <div class="full-width_heading">
                      <h2 class="{{ block.settings.full_width_heading_size }}">{{ block.settings.full_width_heading }}</h2>
                    </div>
                  {% endif %}
                  {% if block.settings.full_width_description !=blank %}
                    <div class="full-width_text">
                      {{ block.settings.full_width_description }}
                    </div>
                  {% endif %}
                </div>
              </div>
            {%- endcase -%}
        {% endfor %}

      <div class="two-cloumn-section">
        <div class="left-block_row">
          {%- for block in section.blocks -%}
            {% case block.type %}
              {%- when 'leftblock' -%}
                <div class="content-block_cover block-{{ block.id }}" {{ block.shopify_attributes }}>
                  {% if block.settings.left_block_heading !=blank %}
                    <div class="inr-heading">
                      <h3 class="{{ block.settings.left_block_heading_size }}">{{ block.settings.left_block_heading }}</h3>
                    </div>
                  {% endif %}
                  {% if block.settings.left_block_description !=blank %}
                    <div class="inr-description">
                      {{ block.settings.left_block_description }}
                    </div>
                  {% endif %}
                </div>
            {%- endcase -%}
          {% endfor %}
        </div>
        <div class="right-block_row">
          {%- for block in section.blocks -%}
            {% case block.type %}
              {%- when 'rightblock' -%}
                <div class="content-block_cover block-{{ block.id }}" {{ block.shopify_attributes }}>
                  {% if block.settings.right_block_heading !=blank %}
                    <div class="inr-heading">
                      <h3 class="{{ block.settings.right_block_heading_size }}">{{ block.settings.right_block_heading }}</h3>
                    </div>
                  {% endif %}
                  {% if block.settings.right_block_description !=blank %}
                    <div class="inr-description">
                      {{ block.settings.right_block_description }}
                    </div>
                  {% endif %}
                </div>
            {%- endcase -%}
          {% endfor %}
        </div>
      </div>
      
    </div>
    
  </div>
</div>

{% schema %}
{
  "name": "Seo Section",
  "tag": "section",
  "class": "section seo-section",
  "disabled_on": {
    "groups": ["header", "footer"]
  },
  "settings": [
    {
      "type": "checkbox",
      "id": "full_width",
      "default": true,
      "label": "Full witdh"
    },
    {
        "type": "range",
        "id": "page_width",
        "min": 1000,
        "max": 1600,
        "step": 100,
        "default": 1200,
        "unit": "px",
        "label": "Page width"
      },
     {
      "type": "color",
      "id": "link_color",
      "label": "Link color",
      "default": "#000000"
    },
    {
      "type": "header",
      "content": "Section padding"
    },
    {
      "type": "range",
      "id": "padding_top",
      "min": 0,
      "max": 100,
      "step": 4,
      "unit": "px",
      "label": "Top padding",
      "default": 40
    },
    {
      "type": "range",
      "id": "padding_bottom",
      "min": 0,
      "max": 100,
      "step": 4,
      "unit": "px",
      "label": "Bottom padding",
      "default": 52
    }
  ],
  "blocks": [
    {
      "type": "fullwidthblock",
      "name": "Full width block",
      "limit": 1,
      "settings": [
        {
          "type": "textarea",
          "id": "full_width_heading",
          "default": "Talk about your brand",
          "label": "Heading"
        },
        {
          "type": "richtext",
          "id": "full_width_description",
          "default": "<p>Share information about your brand with your customers. Describe a product, make announcements, or welcome customers to your store.</p>",
          "label": "Description"
        },
        {
          "type": "color",
          "id": "full_width_heading_color",
          "label": "Heading color",
          "default": "#000000"
        },
        {
          "type": "color",
          "id": "full_width_description_color",
          "label": "Heading color",
          "default": "#000000"
        },
        {
          "type": "select",
          "id": "full_width_heading_size",
          "options": [
            {
              "value": "h1",
              "label": "h1"
            },
            {
              "value": "h2",
              "label": "h2"
            },
            {
              "value": "h3",
              "label": "h3"
            },
            {
              "value": "h4",
              "label": "h4"
            },
            {
              "value": "h5",
              "label": "h5"
            },
            {
              "value": "h6",
              "label": "h6"
            }
          ],
          "default": "h1",
          "label": "Heading size"
        },
        {
          "type": "range",
          "id": "full_desktop_description_size",
          "min": 0,
          "max": 26,
          "step": 2,
          "unit": "px",
          "label": "Desktop description font size",
          "default": 18
        },
        {
          "type": "range",
          "id": "full_mobile_description_size",
          "min": 0,
          "max": 22,
          "step": 1,
          "unit": "px",
          "label": "Mobile description font size",
          "default": 15
        }
      ]
    },
    {
    "type": "leftblock",
    "name": "Left block",
    "settings": [
      {
        "type": "textarea",
        "id": "left_block_heading",
        "default": "Talk about your brand",
        "label": "Heading"
      },
      {
        "type": "richtext",
        "id": "left_block_description",
        "default": "<p>Share information about your brand with your customers. Describe a product, make announcements, or welcome customers to your store.</p>",
        "label": "Description"
      },
        {
          "type": "color",
          "id": "left_block_heading_color",
          "label": "Heading color",
          "default": "#000000"
        },
        {
          "type": "color",
          "id": "left_block_description_color",
          "label": "Heading color",
          "default": "#000000"
        },
      {
        "type": "select",
        "id": "left_block_heading_size",
        "options": [
          {
            "value": "h1",
            "label": "h1"
          },
          {
            "value": "h2",
            "label": "h2"
          },
          {
            "value": "h3",
            "label": "h3"
          },
          {
            "value": "h4",
            "label": "h4"
          },
          {
            "value": "h5",
            "label": "h5"
          },
          {
            "value": "h6",
            "label": "h6"
          }
        ],
        "default": "h1",
        "label": "Heading size"
      },
      {
          "type": "range",
          "id": "left_desktop_description_size",
          "min": 0,
          "max": 26,
          "step": 2,
          "unit": "px",
          "label": "Desktop description font size",
          "default": 18
        },
        {
          "type": "range",
          "id": "left_mobile_description_size",
          "min": 0,
          "max": 22,
          "step": 1,
          "unit": "px",
          "label": "Mobile description font size",
          "default": 15
        }
    ]
  },
    {
    "type": "rightblock",
    "name": "Right block",
    "settings": [
      {
        "type": "textarea",
        "id": "right_block_heading",
        "default": "Talk about your brand",
        "label": "Heading"
      },
      {
        "type": "richtext",
        "id": "right_block_description",
        "default": "<p>Share information about your brand with your customers. Describe a product, make announcements, or welcome customers to your store.</p>",
        "label": "Description"
      },
      {
        "type": "color",
        "id": "right_block_heading_color",
        "label": "Heading color",
        "default": "#000000"
      },
      {
        "type": "color",
        "id": "right_block_description_color",
        "label": "Heading color",
        "default": "#000000"
      },
      {
        "type": "select",
        "id": "right_block_heading_size",
        "options": [
          {
            "value": "h1",
            "label": "h1"
          },
          {
            "value": "h2",
            "label": "h2"
          },
          {
            "value": "h3",
            "label": "h3"
          },
          {
            "value": "h4",
            "label": "h4"
          },
          {
            "value": "h5",
            "label": "h5"
          },
          {
            "value": "h6",
            "label": "h6"
          }
        ],
        "default": "h1",
        "label": "Heading size"
      },
      {
        "type": "range",
        "id": "right_desktop_description_size",
        "min": 0,
        "max": 26,
        "step": 2,
        "unit": "px",
        "label": "Desktop description font size",
        "default": 18
        },
        {
          "type": "range",
          "id": "right_mobile_description_size",
          "min": 0,
          "max": 22,
          "step": 1,
          "unit": "px",
          "label": "Mobile description font size",
          "default": 15
        }
    ]
  }
  ],


  
  "presets": [
    {
      "name": "Seo Section",
      "blocks": [
        {
          "type": "fullwidthblock"
        },
         {
          "type": "leftblock"
        },
         {
          "type": "rightblock"
        }
      ]
    }
  ]
}
{% endschema %}
