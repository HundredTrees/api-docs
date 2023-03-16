Usage
=====

.. _setup:

Setup
-----

First, register_ or login_ on HundredTrees. Then go in your settings, and copy your private API key.

.. _register: https://dashboard.hundredtrees.com/#/signup
.. _login: https://dashboard.hundredtrees.com/#/login

Estimating CO₂e emissions
-------------------------

Single product
++++++++++++++

To estimate the CO₂e emissions for a single product, use the route ``/estimate-product``::

    curl -X POST 'https://api.hundredtrees.com/v0/estimate-product' \
      -H 'Content-Type: application/json' \
      -H 'X-HT-Token: YOUR_API_KEY' \
      -d '{
            "name": "My Awesome Shirt",
            "category": "cotton_shirt",
            "weight_kg": 0.120,
            "quantity": 2,
            "country_from": "IND",
            "country_to": "ESP"
          }'

In the example above, we’re estimating the CO₂e emissions for two cotton shirts with an approx weight of 120g made in
India (``IND``) and shipped to Spain (``ESP``).

.. note::

    You can configure the default countries of origin and delivery in your admin dashboard.

The result looks like this::

    {
      "production": {
        "weight_kg": 8.0
      },
      "shipping": {
        "weight_kg": 0.045
      },
      "total": {
        "weight_kg": 8.045
      }
    }

The above means the estimated emissions for these shirts is 8 kg of CO₂e for the production and 45 g for the shipping.


Multiple products
+++++++++++++++++

To estimate the CO₂e emissions of multiple units of the same product, use the route for a `single product`_ and use the
``quantity`` field. If the units are of different products, use ``/estimate-products``. The route follows the same
format as ``/estimate-product`` except that both its input and its output are lists. This is equivalent to
repeatedly calling the single-product route but in a single API call.

Orders
++++++

*TODO*

Compensating for CO₂e emissions
-------------------------------

*TODO*
