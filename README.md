# NuCo = Nutritional Code
Why search for a special product if you only need the calories or ingredients ? Just scan a QR-code!

### Proposal:

For processed foods, instead of searching for a specific product (e.g.yogurt of a certain brand), we just want to encode the nutritional information in both a human readable code and a machine readable code.

### Example:


Chobani Vanilla Blended Non-Fat Greek Yogurt (32 oz)
For 100g product, this means:

calories:57kcal
fat: 0g
carbs:6g
protein:14g

We can just process the properties of this chart into JSON:

{
  calories: 57,
  fat: 0,
  carbs:6,
  protein:14,
}

The units could be implicit. Then use `JSON.stringify()` and encode this string into a qr code:

![Nutritional Value JSON in QR Form](https://github.com/TetsuGuy/nuco/blob/master/QRCode.PNG)

People can then just weigh the amount of food they want to consume from this product with a kitchen scale.
The QR-Code/Reader is easy to include in fitness/health/diet-apps and people would only need to search for unprocessed foods without
nutritional labe (e.g. "Potato", "Apple").

### Side Note:

When i came up with this idea, originally i thought of Google's way to encode a specific Point in Google Maps to like 3 words of human readable language.
For example, the point of White House, Washington would be: 38°53'51.7"N 77°02'11.5"W encoded into "dog banana three". 
Similar to this approach: https://tools.ietf.org/html/rfc1751 for remembering passwords.

### Room for improvement:

The JSON Object Notation is not necessarily the best option. Just as well there could be just the array of numbers, as long as we are able to infer what kind of nutritional key the number is assigned to.

{
  calories: 57,
  fat: 0,
  carbs:6,
  protein:14,
}

would become:

57,,6,14

or as QR Code:

![Nutritional Value JSON in QR Form smaller](https://github.com/TetsuGuy/nuco/blob/master/QRCode2.PNG)


Index | Nutritional Value
------------ | -------------
0 | calories
1 | carbs
2 | fat
3 | protein
4-99 | ?


### NuCo-Scale

I want to make a Scale with a small glass window in the middle to scan NuCos. After the scan, i could either just weigh the amount of product or chose a measuring method.
I could think about 3 workflows:

#### 1.) Auto / by weight

The calories are displayed for the amount of product you are currently weighing

#### 2.) Total / by unit

The calories are displayed for the whole package. (Imagine a cup of yoghurt with fruit from a brand).

Many products come with info about portion calorie count but since we are lazy we just scan it and it gets displayed.

#### 3.) Add + a combination of 1.) or 2.)

Add/Auto: continious scanning and weighing of products to get a total calorie count at the end

Add/Total: continous scanning to get a total calorie count at the end

#### What about Apples?

There are (thankfully) many unprocessed products, like fruit and vegetables. I doubt it would be a good solution to put another NuCo sticker on each of them. Maybe a simple database of those foods could be integrated into products like calorie counter apps or the mentioned NuCo Scale. Or if you are shopping, the supermarket can put a NuCo above the apple crate to scan or take a pic of.


