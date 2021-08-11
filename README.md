# QuirkSWT
QuirkSWT *warps* Java SWT as quirk as no one has made before; here some planned usage examples:

```java
// create a preset with two properties for using later
QuirkSWT preset1 = QuirkSWT.newPreset().setAlign("BASELINE_LEFT").setText("default text");

// create a preset with one property and including other preset for using later
QuirkSWT preset2 = QuirkSWT.newPreset().setTextAlign(QuirkSWT.JUSTIFY).setPreset(preset1);

// create a image
QuirkSWT img = QuirkSWT.newImage("test.png");

// create label and set properties
QuirkSWT lbl = QuirkSWT.newLabel().setPreset(preset2).setText("label text")
		.setImage(img).setTextAlign("JUSTIFY");

// obtain the "warped" original SWT reference
Label lblswt = lbl.get(Label.class);

// create a button with the previous labels as reference
Button btnswt = QuirkSWT.newButton().setText("button1").get(Button.class);

// get back the lbl text property
String lbltext = lbl.get(QuirkSWT.Type.TEXT, String.class);
// or same like this
lbltext = lbl.getText();

// pickup again the previous created SWT button and set a backgroundcolor and another text
QuirkSWT.warp(btnswt).setBackground(255, 0, 0).setText("this is a button");
```
Plans are finishing support for all or at least most used properties (using PipeCC precompiler) and, also including a simplified but superpowerful context-aware Q-notation for constructors:

```java
Q preset1 = Q.preset().align(Q.BASELINE_LEFT).text("default text");
Q preset2 = Q.preset().textAlign(Q.JUSTIFY).preset(preset1);
Q img = Q.image("test.png");
Q lbl = Q.label().preset(preset2).text("label text").image(img).textAlign("JUSTIFY");
Label lblswt = lbl.get(Label.class);
Button btnswt = Q.button().text("button1").get(Button.class);
String lbltext = lbl.get(Q.TEXT, String.class);
lbltext = lbl.text(); // do the same that previous line
Q.warp(btnswt).background(255, 0, 0).text("this is a button");
```
