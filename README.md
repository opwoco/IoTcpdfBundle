How to Install
==============

Add IoTcpdfBundle in your composer.json:

```js
{
    "require": {
        "gayalab/tcpdfbundle": "dev-master"
    }
}
```

Now tell composer to download the bundle by running the command:

``` bash
$ php composer.phar update
```

Composer will install the bundle to your project's `vendor/gayalab` directory.

### Step 2: Enable the bundle

Enable the bundle in the kernel:

``` php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Io\TcpdfBundle\IoTcpdfBundle(),
    );
}
```


HOW TO USE:
==============
Controller: mybundle/controllers/myController.php
``` php
        class MyController extends Controller
        {
            /**
             * @Route("/mypage.pdf")
             */
            public function mypageAction()
            {
                //creating html source
                $html = $this->renderView('MyBundle:MyController:mypage.pdf.twig', array());

                //loading io_tcpdf library
                $pdf = $this->get('io_tcpdf');
                //do your stuff here
                    
                //display pdf (it returns a Response Object)
                return $pdf->quick_pdf($html);
            }
        }
```

View: mybundle/Resources/views/myController/mypage.pdf.twig
``` html
<div><h1>header</h1></div>
<hr />
<div>content</div>
```

TODO
============

 * smart method for easier PDF generation and customization
 * cache pdf generation
 * @PDF('template.twig') annotation system