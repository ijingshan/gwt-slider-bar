## Usage of SliderBars ##

Then SliderBar is created it is time to start use it.

Minimal set of steps for create abd usage SliderBar:

  * Create Your implementation of SliderBar ( not absolutly necessary - You can use earlier predefined SliderBar from some kind of SliderBar library )

  * Create SliderBar instance

  * Set width of SliderBar for SliderBarHorizontal or height for SliderBarVertical

  * Set integer value, which corresponds to rightmost position of Drag wiidget (knob) for horizontal SliderBar or for bottommost position of Drag widget  for vertical SliderBar

  * Add event listener fo react to change position of Drag widget (knob)

  * Place SliderBar to screen

**_Code samples for illlustrate this steps and another use cases_**

_Creating implementation of SliderBar_

```
public class SliderBarSimpleVertical extends SliderBarVertical {
	
	ImagesSliderBarSimpleVertical images = GWT.create(ImagesSliderBarSimpleVertical.class);

	public SliderBarSimpleVertical(int maxValue, String height, boolean showRows) {		
		if (showRows){
			setLessWidget(new Image(images.less()) );
			setScaleWidget(new Image(images.scalev().getUrl()), 10);
			setMoreWidget(new Image(images.more()));
		} else {
		    setScaleWidget(new Image(images.scalev().getUrl()), 10);
		}
		setDragWidget(new Image(images.drag()));
		this.setHeight(height);
		this.setMaxValue(maxValue);		
	}

	interface ImagesSliderBarSimpleVertical extends ClientBundle{
		
		@Source("dragvthin.png")
		ImageResource drag();

		@Source("minus.png")
		ImageResource less();

		@Source("plus.png")
		ImageResource more();

		@Source("scalevthinblack.png")
		DataResource scalev();				
	}
	
}
```

_Creating instance of SliderBar and seting height and max integer value, which corresponds to bottommost drag position_
```
...
SliderBarSimpleVertical sliderBarSimpleVertical = 
			new SliderBarSimpleVertical(maxValue, width,  true);
...
```

_Adding event listener_
```
                ...
		sliderBarSimpleVertical
		.addBarValueChangedHandler(new BarValueChangedHandler() {
			public void onBarValueChanged(BarValueChangedEvent event) {
				valueBox.setValue("" + event.getValue());
			}
		});		
                ...
```

_Show scale marks_
```
                ...
                sliderBar.drawMarks("white",6);
                ...
```
With help of above method it is possible to display scale mark. Scale mark is simple line (horizontal line for Vertical SliderBar or vertical line for Horizontal SliderBar). It is possible to set color and size of scale mark. The marks will be drawn if distance beetveen neighbouring mark in pixels more then some predetermined value. To ajust this value You have to use method
```
                ...
                sliderBar.setMinMarkStep(3);
                ...

```

_Set presence or absence of outline border vhen SliderBar widget is in focus_

By default outline border presents when SliderBar is in focus. To turn off this feature You have to use method:
```
                ...
                sliderBar.setNotSelectedInFocus(); 
                ...
```

_Change Drag element (knob) position programmaticaly_

```
                 sliderBar.setValue(valueInt);
```

_Change max value programmaticaly_

```
                 ...
                 sliderBar.setMaxValue(valueInt);
                 ... 
```

You can see above method in action by explore interractive sample in demo application