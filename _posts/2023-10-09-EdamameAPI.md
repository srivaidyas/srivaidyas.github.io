---
toc: True
comments: False
layout: post
title: Edamam Api
type: tangibles
courses: {'compsci': {'week': 8}}
---

```python
import requests

# Replace 'YOUR_APP_ID' and 'YOUR_APP_KEY' with your actual Edamam API key
APP_ID = '9d5f6314'
APP_KEY = '6402f0a5647c2c2bb72cb3bb592d0c8b'

# Edamam Recipe Search API endpoint
api_endpoint = 'https://api.edamam.com/search'

# Query parameters
params = {
    'q': 'chicken',  # Search query (you can modify this)
    'app_id': APP_ID,
    'app_key': APP_KEY,
}

# Make the API request
response = requests.get(api_endpoint, params=params)

# Check if the request was successful (status code 200)
if response.status_code == 200:
    # Parse and print the response JSON
    data = response.json()
    for hit in data.get('hits', []):
        recipe = hit.get('recipe', {})
        print(f"Recipe: {recipe.get('label')}")
        print(f"Ingredients: {', '.join(recipe.get('ingredientLines', []))}")
        print(f"URL: {recipe.get('url')}")
        print("\n" + "=" * 30 + "\n")
else:
    # Print an error message if the request was not successful
    print(f"Error: {response.status_code} - {response.text}")

```

    Recipe: Chicken Vesuvio
    Ingredients: 1/2 cup olive oil, 5 cloves garlic, peeled, 2 large russet potatoes, peeled and cut into chunks, 1 3-4 pound chicken, cut into 8 pieces (or 3 pound chicken legs), 3/4 cup white wine, 3/4 cup chicken stock, 3 tablespoons chopped parsley, 1 tablespoon dried oregano, Salt and pepper, 1 cup frozen peas, thawed
    URL: http://www.seriouseats.com/recipes/2011/12/chicken-vesuvio-recipe.html
    
    ==============================
    
    Recipe: Chicken Paprikash
    Ingredients: 640 grams chicken - drumsticks and thighs ( 3 whole chicken legs cut apart), 1/2 teaspoon salt, 1/4 teaspoon black pepper, 1 tablespoon butter – cultured unsalted (or olive oil), 240 grams onion sliced thin (1 large onion), 70 grams Anaheim pepper chopped (1 large pepper), 25 grams paprika (about 1/4 cup), 1 cup chicken stock, 1/2 teaspoon salt, 1/2 cup sour cream, 1 tablespoon flour – all-purpose
    URL: http://norecipes.com/recipe/chicken-paprikash/
    
    ==============================
    
    Recipe: Baked Chicken
    Ingredients: 6 bone-in chicken breast halves, or 6 chicken thighs and wings, skin-on, 1/2 teaspoon coarse salt, 1/2 teaspoon Mrs. Dash seasoning, 1/4 teaspoon freshly ground black pepper
    URL: http://www.marthastewart.com/318981/baked-chicken
    
    ==============================
    
    Recipe: Catalan Chicken
    Ingredients: 1 whole 4-pound chicken, quartered, 8 slices bacon, 30 cloves garlic, 3 lemons, peeled, rinds thinly sliced and reserved, ½ cup Banyuls or another fortified dessert wine, 1 cup veal or chicken stock
    URL: http://www.bonappetit.com/columns/breadwinner/article/how-to-get-your-kids-to-eat-sauce-let-them-cook-it-themselves
    
    ==============================
    
    Recipe: Chicken Stew
    Ingredients: 1 pound chicken cut in pieces, 4 carrots, 1 onion, 1 leek, 1 green pepper, kosher salt, Freshly ground black pepper, Extra Virgin Olive Oil, 1 cup white wine, Chicken broth
    URL: https://food52.com/recipes/83097-chicken-stew
    
    ==============================
    
    Recipe: Chicken Liver Pâté
    Ingredients: 8 oz. chicken livers, cleaned, 4 cups chicken stock, 2 tbsp. rendered chicken fat or unsalted butter, ½ medium yellow onion, minced, 1½ tbsp. cognac or brandy, 2 hard-boiled eggs, Kosher salt and freshly ground black pepper, to taste, Toast points, for serving
    URL: http://www.saveur.com/article/Recipes/Classic-Chicken-Pate
    
    ==============================
    
    Recipe: Persian Chicken
    Ingredients: 2 large onions, 750 g chicken, 500 g mushrooms, 1 cup water, 1 cup red wine, 2 teaspoons chicken stock, 200 ml mayonnaise, 200 ml cream, small bunch of parsley, 1 teaspoon curry powder
    URL: http://www.bbcgoodfood.com/recipes/7343/
    
    ==============================
    
    Recipe: Kreplach (Chicken Dumplings)
    Ingredients: 1½ teaspoons canola oil, ½ small shallot, finely chopped, 1 cup (about ½ pound) raw, boneless chicken meat (preferably from 3 boneless chicken thighs), roughly chopped, ⅔ cup (about ¼ pound) chicken skin and fat (reserved from the 3 chicken thighs), 2 chicken livers (optional), 2 garlic cloves, finely chopped, ¼ cup finely chopped chives, plus extra for serving, 1¼ teaspoons kosher salt, ¾ teaspoon freshly ground black pepper, 30 to 34 square wonton wrappers, 8 cups store-bought or homemade chicken broth
    URL: https://www.tastingtable.com/entry_detail/chefs_recipes/10154/Matzo_balls_watch_your_back.htm
    
    ==============================
    
    Recipe: Chicken cacciatore
    Ingredients: 8 tbsp olive oil, 1 onion, sliced, 2 celery stalks, roughly chopped, 2 medium carrots, roughly chopped, 6 chicken breasts, or chicken thighs, bones removed, 175ml/6fl oz white wine, 3 tbsp tomato purée, 500ml/17 fl oz chicken stock, 2 bay leaves, 2-3 sage leaves, 1 rosemary sprig, 250g/9oz easy-cook polenta, Knob of butter, 25g/1oz parmesan
    URL: http://www.bbc.co.uk/food/recipes/chickenalocacciatore_70349
    
    ==============================
    
    Recipe: Roast Chicken
    Ingredients: 1 whole chicken, about 3-4 pounds, -- Salt and fresh-ground pepper, to taste, 3 to 4 sprigs thyme, or other herbs, -- Olive oil, to taste, -- Chicken stock (optional)
    URL: http://www.sfgate.com/food/recipes/detail.html?rid=18229&sorig=qs
    
    ==============================
    

