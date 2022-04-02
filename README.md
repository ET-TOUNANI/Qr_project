# Qr_Generator <img src="https://github.com/ET-TOUNANI/Qr_project/blob/master/images/download.jpg" >
using phpqrcode library 

## code 
include('phpqrcode/qrlib.php');

    // how to save PNG codes to server
    
    $tempDir = "images/";
    
    $codeContents = 'salam Qr';
    
    // we need to generate filename somehow, 
    // with md5 or with database ID used to obtains $codeContents...
    $fileName = '005_file_'.md5($codeContents).'.png';
    
    $pngAbsoluteFilePath = $tempDir.$fileName;
    $urlRelativeFilePath = $tempDir.$fileName;
    
    // generating
    if (!file_exists($pngAbsoluteFilePath)) {
        QRcode::png($codeContents, $pngAbsoluteFilePath);
        echo 'File generated!';
        echo '<hr />';
    } else {
        echo 'File already generated! We can use this cached file to speed up site on common codes!';
        echo '<hr />';
    }
    
    echo 'Server PNG File: '.$pngAbsoluteFilePath;
    echo '<hr />';
    QRcode::png('PHP QR Code :)');
    // displaying
    echo '<img src="'.$urlRelativeFilePath.'" />';
