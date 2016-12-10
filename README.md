# Color Picker
## Simple color picker dialog for iOS/swift

ColorPicker is a simple, custom UIView that can be used to prompt the user to select a color. It also offers a zoom-like preview while the user's finger is down and moving.

###Preview
![iOS Swift Color Picker Preview](./preview.gif)

### Usage
1. Add the `ColorPicker` class to your project.
2. Add the `ColorPickerDelegate` delegate to your view controller.
3. Implement `ColorColorPickerTouched` in your view controller
4. Create a new instance of `ColorPicker` and add it your view
5. Set the delegate for the color picker instance.


### Code Sample
	class ViewController: UIViewController, ColorPickerDelegate
	{
		@IBOutlet weak var button: UIButton!
		
		override func viewDidLoad()
		{
			super.viewDidLoad()
			// Do any additional setup after loading the view, typically from a nib.
		}
	
		override func didReceiveMemoryWarning()
		{
			super.didReceiveMemoryWarning()
			// Dispose of any resources that can be recreated.
		}
	
		
		@IBAction func setColor(_ sender: UIButton)
		{
			let pickerWidth = self.view.frame.size.width
			let pickerHeight = (pickerWidth * 11) / 19
			let colorPicker = ColorPicker(frame: CGRect(
				x: 0,
				y: self.view.frame.size.height / 2 - pickerHeight / 2,
				width: pickerWidth,
				height: pickerHeight
			))
			
			colorPicker.delegate = self
			
			self.view.addSubview(colorPicker)
		}
		
		func ColorColorPickerTouched(sender: ColorPicker, color: UIColor, point: CGPoint, state: UIGestureRecognizerState)
		{
			button.backgroundColor = color
			sender.removeFromSuperview()
		}
	} 