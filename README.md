# Simple Tools

>  A repository for storing tools

## Demo

* [demo.php](./demo.php)

## List & Usage

###### 1. FViewCreator - A Simple Tool For Create Html/Xml Code  `FViewCreator/FViewCreator.php`

   ```php
use HappyStraw\FViewCreator as FVC;
$str = FVC::make('div')
        ->setAttr('id', 'div1')
        ->setAttr(['style' => 'width:70px', 'class' => 'class1'])
        ->append('<h1>title</h1>')
        ->append(
            FVC::make('ul')
            ->setAttr(
                'data-parentid="1"'
            )->append(
                FVC::make('li')->append('menu1')
            )->append(
                ['tag' => 'li', 'attr' => 'data-id="2"', 'inner' => 'menu2']
            )->append(
                [
                    ['tag' => 'li', 'inner' => '<b>menu3</b>'],
                    ['tag' => 'li', 'inner' => [FVC::make()->append('menu'), '4']],
                    FVC::make('li')->append('menu5')
                ]
            )
        )->append(
            [
                FVC::make('tag1', ['id' => 'tag1'], ['item in tag1']),
                FVC::make('tag2', '', 'inner is not valid')->close(true),
                FVC::make('input', 'readonly', 'inner is not valid')
            ]
        )->fetch();
echo $str;
// output(reindent):
// <div id="div1" style="width:70px" class="class1">
//   <h1>title</h1>
//   <ul data-parentid="1">
//     <li>menu1</li>
//     <li data-id="2">menu2</li>
//     <li><b>menu3</b></li>
//     <li>menu4</li>
//     <li>menu5</li>
//   </ul>
//   <tag1 id="tag1">item in tag1</tag1>
//   <tag2/>
//   <input readonly/>
// </div>
   ```

## Dependencies

* [php](http://php.net/) >= 5.4

## Licence

simple-tools is open source and released under the MIT Licence.

Copyright (c) 2017 FangYutao