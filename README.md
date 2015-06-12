# AboutAnimation3
基于Transform的动画

/*********************记住自己熟练的使用即可************************/

//
//  ViewController.h
//  Lesson-UITransform
//
//  Created by 林梓成 on 15/6/12.
//  Copyright (c) 2015年 lin. All rights reserved.
//

#import <UIKit/UIKit.h>

@interface ViewController : UIViewController

@property (weak, nonatomic) IBOutlet UIView *view1;

- (IBAction)doButton1:(id)sender;

- (IBAction)doButton2:(id)sender;

@end


//
//  ViewController.m
//  Lesson-UITransform
//
//  Created by 林梓成 on 15/6/12.
//  Copyright (c) 2015年 lin. All rights reserved.
//

#import "ViewController.h"

@interface ViewController ()

@end

@implementation ViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    // Do any additional setup after loading the view, typically from a nib.
    
    // 基于transform的旋转动画是围绕锚点来旋转的而不是中心点
    self.view1.layer.anchorPoint = CGPointMake(0, 0.8);
}

- (void)didReceiveMemoryWarning {
    [super didReceiveMemoryWarning];
    // Dispose of any resources that can be recreated.
}

- (IBAction)doButton1:(id)sender {
    
    [UIView animateWithDuration:2 animations:^{
       
        // 1、基于transform的平移动画(1次)（创建一个transform的形变量）
        //CGAffineTransform t_maketranslation = CGAffineTransformMakeTranslation(100, 100);
        //self.view1.transform = t_maketranslation;
        
        // 2、基于transform的连续平移动画（参数1:对谁做连续的操作）
        //CGAffineTransform t_translation = CGAffineTransformTranslate(self.view1.transform, 100, 100);
        //self.view1.transform = t_translation;
        
        // 3、基于transform的一次旋转效果
        //CGAffineTransform t_makeRotation = CGAffineTransformMakeRotation(M_PI/6);
        //self.view1.transform = t_makeRotation;
        
        // 4、基于transform的连续旋转动画
        CGAffineTransform t_rotation = CGAffineTransformRotate(self.view1.transform, M_PI/7);
        self.view1.transform = t_rotation;
        
        // 5、基于transform的一次形变动画
        //CGAffineTransform t_makeScale = CGAffineTransformMakeScale(1, 0.5);
        //self.view1.transform = t_makeScale;
        
        // 6、基于transform的连续形变动画
        CGAffineTransform t_scale = CGAffineTransformScale(self.view1.transform, 1, 0.5);
        self.view1.transform = t_scale;
        
        // 7、合并两个仿射变化（数学矩阵相乘）
        CGAffineTransform t_t = CGAffineTransformConcat(t_rotation, t_scale);
        self.view1.transform = t_t;
        
    }];
    
}

- (IBAction)doButton2:(id)sender {
    
    /*
    [UIView animateWithDuration:1 animations:^{
        
        self.view1.layer.transform = CATransform3DRotate(self.view1.layer.transform, M_PI/3, 1, 1, 1);
        
    }];
    */
    
    [NSTimer scheduledTimerWithTimeInterval:1 target:self selector:@selector(dotime) userInfo:nil repeats:YES];
    
    
}

- (void)dotime {
    
    self.view1.layer.transform = CATransform3DRotate(self.view1.layer.transform, M_PI/30, 0, 0, 1);
}



@end
