ios-spritekit-snippets
======================

##Description

This repo simply contains sample code for using the SpriteKit framework.

![icon](imgs/spritekit-icon.png)

##Languages

Swift and Objective-C

##Snippets

At the time of this writing, a majority of the SpriteKit framework documentation was written with code samples in __Objective-C__.  The snippets below translate various SpriteKit patterns using __Swift__.

####Adding a sprite primitive to a Scene

___Swift___

````
    let spriteNode = SKSpriteNode(color: SKColor.redColor(), size: CGSize(width: 100, height: 100))
    spriteNode.name = "redSquare"
    spriteNode.position = CGPointMake(CGRectGetMinX(self.frame) + 100, CGRectGetMaxY(self.frame) - 100
    self.addChild(spriteNode)
    
````
___Objective-C___

````
    SKSpriteNode *spriteNode = [[SKSpriteNode alloc] initWithColor:[SKColor redColor] size:CGSizeMake(100, 100)];
    spriteNode.name = @"redSquare";
    spriteNode.position = CGPointMake(CGRectGetMaxX(self.frame) - 100, CGRectGetMinY(self.frame) + 150);
    [self addChild:spriteNode];
    
````

####Adding a sprite with an image/texture to a Scene

___Swift___

````
	let backgroundSpaceNode = SKSpriteNode(imageNamed: "spacebackground")
    backgroundSpaceNode.position = CGPointMake(self.size.width/2, self.size.height/2)
    backgroundSpaceNode.zPosition = -1
    self.addChild(backgroundSpaceNode)
````

___Objective-C___

````
    SKSpriteNode *backgroundSpaceNode = [SKSpriteNode spriteNodeWithImageNamed:@"spacebackground"];
    backgroundSpaceNode.position = CGPointMake(self.size.width/2, self.size.height/2);
    backgroundSpaceNode.zPosition = -1;
    [self addChild:backgroundSpaceNode];
````

####Playing a sound file in a Scene

___Swift___

````
	let soundAction = SKAction.playSoundFileNamed("space-ambient.wav", waitForCompletion: true);
    
    //play once
    scene.runAction(soundAction)

    //play and repeat forever
    //self.runAction(SKAction.repeatActionForever(soundAction))
        
````

___Objective-C___

````
	SKAction *soundAction = [SKAction playSoundFileNamed:@"space-ambient.wav" waitForCompletion:YES];
    
    //play once
    [self runAction:soundAction];
    
    //play and repeat forever
    //[self runAction:[SKAction repeatActionForever:soundAction]];
````

####Applying an Action (e.g. Move) to a Sprite Node in a Scene

___Swift___

````
	let moveAction = SKAction.moveByX(100.0, y:0.0, duration: 4.0)
    
    spaceshipNode.runAction(moveAction)
        
````

___Objective-C___

````
	SKAction *moveAction = [SKAction moveByX:100.0 y:0.0 duration:4.0];
	
	[spaceshipNode runAction:moveAction];

````

####Applying a Sequence of Actions to a Sprite Node in a Scene

___Swift___

````
    let hover = SKAction.sequence([SKAction.waitForDuration(0.5),
        SKAction.moveByX(0.0, y:10.0, duration:1.0),
        SKAction.moveByX(0.0, y:5.0, duration:1.0),
        SKAction.waitForDuration(0.5),
        SKAction.moveByX(0.0, y:-10.0, duration:1.0),
        SKAction.moveByX(0.0, y:-5.0, duration:1.0)])
        
    spaceshipNode.runAction(SKAction.repeatActionForever(hover))
        
````

___Objective-C___

````
	SKAction *hover = [SKAction sequence:@[
                                [SKAction waitForDuration:0.5],
                                [SKAction moveByX:0.0 y:10.0 duration:1.0],
                                [SKAction moveByX:0.0 y:5.0 duration:1.0],
                                [SKAction waitForDuration:0.5],
                                [SKAction moveByX:0.0 y:-10 duration:1.0],
                                [SKAction moveByX:0.0 y:-5 duration:1.0]]];
                                
    [spaceshipNode runAction: [SKAction repeatActionForever:hover]];
    
````

####Configuring the Physics Body property of a Sprite Node

___Swift___

````
	spaceshipNode.physicsBody = SKPhysicsBody(circleOfRadius: 75)
    spaceshipNode.physicsBody?.affectedByGravity = false
    spaceshipNode.physicsBody?.mass = 0.02
    
````

___Objective-C___

````
	...
	spaceshipNode.physicsBody = [SKPhysicsBody bodyWithCircleOfRadius:75];
    spaceshipNode.falconNode.physicsBody.affectedByGravity = NO;
    spaceshipNode.falconNode.physicsBody.mass = 0.02;
    
````

####Transitioning Between Scenes

___Swift___

````
	let asteroidScene = AsteroidScene(size: self.frame.size)
	asteroidScene.scaleMode = SKSceneScaleMode.AspectFill
            
	let transition = SKTransition.revealWithDirection(SKTransitionDirection.Down, duration: 1.0)
	self.view?.presentScene(asteroidScene, transition:transition)
            
````

####Handline a User's Touch Gestures on a Scene

___Swift___

````
override func touchesBegan(touches: NSSet, withEvent event: UIEvent) {
        
	//get touch gesture
    let touch: AnyObject? = touches.anyObject()
        
    //get location of touch 
    let location = touch?.locationInNode(self)
        
    //get the node that was touched
    let node = self.nodeAtPoint(location!)
        
    //query for node of interest
    if(node.name == "fireButtonNode") {
            
        //do stuff
        //println("fire")
    }
}
    
override func touchesMoved(touches: NSSet, withEvent event: UIEvent) {
        
	//handle pan gestures (i.e. fingure drags)
}
````

___Objective-C___

````
- (void)touchesBegan:(NSSet *)touches withEvent:(UIEvent *)event {
    
    //get the touch gesture
    UITouch *touch = [touches anyObject];
    
    //get location of touch
    CGPoint location = [touch locationInNode:self];
    
    //get node that was touched
    SKNode *node = [self nodeAtPoint:location];
    
    //query for node of interest
    if([node.name isEqualToString:@"fireButtonNode"]) {
        
        //do stuff...
        //NSLog(@"%@", @"fire!");
    }
}

- (void)touchesMoved:(NSSet *)touches withEvent:(UIEvent *)event {
    
    for (UITouch *touch in touches) {
        
        //get location of touch
        CGPoint location = [touch locationInNode:self];
        
        if([node.name isEqualToString:@"fireButtonNode"]) {
            
            //do stuff
        }
    }
}
````

####Section Name

___Swift___

````
	//todo
````

___Objective-C___

````
	//todo
````

##Connect
* Twitter: [@clintcabanero](http://twitter.com/clintcabanero)
* GitHub: [ccabanero](http:///github.com/ccabanero)