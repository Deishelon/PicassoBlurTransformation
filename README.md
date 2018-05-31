#Blur for Picasso (Android)

- Simple Transformation class to blur an image for Picasso
- Blur time: 1-3 ms*

## Usage

#### Step 1 (Add BlurTransform class to your project)

#### Step 2 (Add to Picasso)

```
Picasso.get().load(YOUR_URL).transform(BlurTransform(scale = 0.1f,radius = 1)).into(YOUR_IMAGE_VIEW)
```

## Docs & Performace & Sample Screenshots
#### Docs
BlurTransform takes 2 parameters
- scale
- radius

###### Scale - scales your bitmap using this formula
```
val width = Math.round(sentBitmap.width * scale)
val height = Math.round(sentBitmap.height * scale)
```
It is recommened not to pass a number higher then 1 (your origial bitmap size), as it will requere extra time to prosses & huge memory allocations

Additional notes:
You can't pass 0, as this will thow an exeption.

###### Radius - radius to blur out pixels

Higher the number - more blur
Very high numbers will increase prossesing time
It is recomened to keep your number between 1 and 50
You can not pass 0, as this will thow an exeption.

#### Screenhots

| Scale  | Radius  |  Output |
| ------------ | ------------ | ------------ |
| 0.1  | 1  | Add image  |
| 0.1  |  10 | Add image   |
| 0.5  |  5 | Add image   |

#### Performace
*Time is milliseconds
*Big bitmaps were used for performnce test (width = 5000px, height = 3000px)

##### Normal usage (down-scale bitmap) Recommended
|   |   |   |   |   |  |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| Scale  | 0.1  | 0.1  | 0.1  |  0.1 | 0.1  |
|  Radius | 1  | 10  | 20  | 50  | 100   |
| Time  | 3  | 6  | 15  |  16 |   35|

It is recommened to use scale between 0.1 and 1

**The Best Performace Between 0.1 And 0.5**


###### No scale, x1

|   |   |   |   |   |  |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| Scale  | 1  | 1  | 1  |  1 | 1  |
|  Radius | 1  | 10  | 20  | 50  | 100   |
| Time  | 48  | 52  | 57  |  82 |   117|

###### Crazy usage, bitmap scaled x5 (not recommened), just for comparisin

|   |   |   |   |   |  |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| Scale  | 5  | 5  | 5  |  5 | 5  |
|  Radius | 1  | 10  | 20  | 50  | 100   |
| Time  | 766  | 886  | 1054  |  1443 |   1581|
