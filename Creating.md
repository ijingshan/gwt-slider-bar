## Creating of SliderBars ##

Before usage, SliderBar must be created . You can create horizontal or vertical SliderBar. It is simple task.

_Note:_<br>
Set of ready to use SliderBars are included to distributed package and You can use this these widgets without creation.<br>
<br>
<br>
For creating horizontal SliderBar You have to use class <i>SliderBarHorizontal</i>.  For creating vertical SliderBar You have to use class <i>SliderBarVertical</i>.Then You have to add all necessary elements (More and Less widgets, scale widget and Drag widget) in the order in which they will be displayed on the screen (for Drag widget order is not important).  For horizontal SliderBar this order is from left to right. For vertical SliderBar this order is from top to bottom.<br>
<br>
<b>Example of horizontal SliderBar creation:</b>

We want create SliderBar which will be look like drawn on picture below.<br>
<br>
<img src='https://lh6.googleusercontent.com/_uimY4ZD7jQU/TVY97GcjoeI/AAAAAAAAAeE/vzyD2uAinQ8/kdelefth.png' />


<b><i>Building blocs of SliderBar</i></b>

<img src='https://lh3.googleusercontent.com/_uimY4ZD7jQU/TVY_Rc6_cyI/AAAAAAAAAeM/hEnoqqk59b8/kdehless.png' /> Less widget<br>
<br>
<img src='https://lh5.googleusercontent.com/_uimY4ZD7jQU/TVY_RjyMC-I/AAAAAAAAAeQ/i5QHZSO6Tgg/kdehmore.png' /> More widget<br>
<br>
<img src='https://lh6.googleusercontent.com/_uimY4ZD7jQU/TVY_RgXJcMI/AAAAAAAAAeU/2b90x50cbM8/kdehdrag.png' /> Drag widget<br>
<br>
<img src='https://lh3.googleusercontent.com/_uimY4ZD7jQU/TVY_RyBFZdI/AAAAAAAAAeY/2rcIgfDeVFM/kdehscale.png' /> Scale widget<br>
<br>
<br>
In this example all above widgets are instances of com.google.gwt.user.client.ui.Image (in common case You can use any other widgets wich corresponds to requirements to widgets, which described on page <a href='CommonInformation.md'>Common information about SliderBars</a>.<br>
<br>
<i>Note:</i>

Scale widget is thin vertical line. This line will be resized with help of <i>setWidth(...)</i> method when we start use this SliderBar.  Similarly, for vertical SliderBar, Scale widget may be represented by thin horizontal line. Resizing of scale of vertical SliderBar will be carried out when we start usage of <i>setHeight(...)</i> method. Other widget will not be resized during SliderBar creation.<br>
<br>
<b><i>Code sample of SliderBar creation:</i></b>

<pre><code>import com.google.gwt.core.client.GWT;<br>
import com.google.gwt.resources.client.ClientBundle;<br>
import com.google.gwt.resources.client.DataResource;<br>
import com.google.gwt.resources.client.ImageResource;<br>
import com.google.gwt.user.client.ui.Image;<br>
import com.kiouri.sliderbar.client.view.SliderBarHorizontal;<br>
<br>
public class KDEHorizontalLeftBW extends SliderBarHorizontal {<br>
	<br>
	ImagesKDEHorizontalLeftBW images = GWT.create(ImagesKDEHorizontalLeftBW.class);<br>
	<br>
	public KDEHorizontalLeftBW(int maxValue, String width) {<br>
	    setLessWidget(new Image(images.less()));<br>
	    setMoreWidget(new Image(images.more()));<br>
	    setScaleWidget(new Image(images.scale().getUrl()), 16);<br>
	    setMoreWidget(new Image(images.more()));<br>
	    setDragWidget(new Image(images.drag()));<br>
	    this.setWidth(width);<br>
	    this.setMaxValue(maxValue);		<br>
	}<br>
		<br>
	interface ImagesKDEHorizontalLeftBW extends ClientBundle {<br>
		<br>
		@Source("kdehdrag.png")<br>
		ImageResource drag();<br>
<br>
		@Source("kdehless.png")<br>
		ImageResource less();<br>
<br>
		@Source("kdehmore.png")<br>
		ImageResource more();<br>
<br>
		@Source("kdehscale.png")<br>
		DataResource scale();<br>
	}	<br>
	<br>
}<br>
</code></pre>