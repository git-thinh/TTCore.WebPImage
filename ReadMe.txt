

public byte[] ConvertWebP(IFormFile image, int quality = 75)
{
    byte[] buf = null;
    if (image == null) return buf;
    if (image.Length == 0) return buf;
    string[] allowedImageTypes = new string[] { "image/jpeg", "image/jpg", "image/png" };
    string type = image.ContentType.ToLower();
    if (!allowedImageTypes.Contains(type)) return buf;            
    try
    {
        //TTCore.WebPImage.Convert.PngToWebP("test.png", "webp.webp", 90);
        //TTCore.WebPImage.Convert.PngToWebPFromWeb("https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png", "webp.webp", 90);
        buf = TTCore.WebPImage.Convert.StreamToWebP(image.OpenReadStream(), quality);
    }
    catch (Exception ex)
    {
    }
    return buf;
}