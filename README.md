
# Greenify - Green Image Filter

Greenify is a simple, single-page web application that allows you to upload an image and apply a vibrant green filter to it. The processed image can then be downloaded directly to your device.

## How to Use the Website

Using Greenify is straightforward:

1.  **Upload Your Image:** You can either click the upload area to select an image from your computer or simply drag and drop an image file onto it.
    
2.  **Preview and Convert:** A preview of your selected image will appear. If you're happy with it, click the "Convert to Green" button.
    
3.  **Download:** The website will process the image and display the green-filtered result. You can then click the "Download Image" button to save it or "Start Over" to try with a new image.
    

## How the "Greenify" Filter Works

The magic happens in the browser using JavaScript and an HTML `<canvas>` element. Here’s a simple breakdown of the process:

1.  **Image to Canvas:** When you click "Convert," your uploaded image is drawn onto a hidden digital canvas. This allows the code to access and manipulate the individual pixels of the image.
    
2.  **Pixel by Pixel:** The code then loops through every single pixel in the image.
    
3.  **Understanding Color:** Each pixel's color is initially represented by **RGB** (Red, Green, Blue) values. However, it's difficult to change a color's hue reliably with RGB. So, the code converts the RGB value of each pixel into **HSL** (Hue, Saturation, Lightness).
    
    -   **Hue**: This is the pure color itself (e.g., red, yellow, green, blue). Think of it as a position on a 360-degree color wheel.
        
    -   **Saturation**: This is the intensity or "purity" of the color. Low saturation results in a grayscale color.
        
    -   **Lightness**: This determines how light or dark the color is, ranging from black to white.
        
4.  **Applying the Green Filter:** With the color in HSL format, applying the filter is easy:
    
    -   The **Hue** of every pixel is changed to `120` degrees, which is the standard value for **green** on the color wheel.
        
    -   The **Saturation** is slightly increased to make the green color more vibrant and less washed out.
        
    -   The original **Lightness** of each pixel is kept the same. This is the key to making it look like a filter, as it preserves the original image's shadows, mid-tones, and highlights.
        
5.  **Finalizing the Image:** After changing the HSL values, the code converts each pixel's color back to the RGB format. This updated pixel data is then put back onto the canvas, revealing the final, "greenified" image, which you can then download.
    

## File Structure

The entire website is self-contained in a single file: `index.html`. This file includes:

-   The HTML structure.
    
-   The CSS for styling (using Tailwind CSS and custom animations).
    
-   All the JavaScript logic for the user interface and image processing.
