# Lawn_Paynes

## Purpose

The Lawn Paynes website is a proposal page for a friend who is looking to expand his small lawn care and landscaping business by showing which services he provides, examples of his work using a slideshow, and a contact page to allow customers to reach out to him. 

## JavaScript Functions


1. `displayMessage()` file: [spring.js](https://github.com/ryansallee/ryansallee.github.io/blob/master/js/spring.js) Page: [Lawn Paynes Home Page](https://ryansallee.github.io/index.html)
- This function's purpose is to insert a message into the `#alert` div on this project's home page that is dependent upon the date listed on the computer detected by JavaScript with the `Date.now()` method saved into the `todayDate` variable in Unix Time as a date object. As well, two dates are saved as date objects in `beginSpringDate` (03/20/2018), the beginning of spring, and `beginSummerDate` (06/21/2018), the beginning of summer, that will determine the messages displayed. If the date is before the beginning of spring, the message stored in `beforeSpringMessage` will display in the `#alert` div set to an orange background. However, if the date is after the beginning of spring but before the beginning of summer, the messsage stored in the `beforeSummerMessage` will display in the `#alert` div set to a red background.
- Testing Notes:
To test the the displayMessage conditions for when it is before spring, please change the date on your computer to a date before 3/20/18, navigate away from the domain, and then return back to the page. You should be able to see the message "Spring is coming! *Call us* now to get your Lawn Paynes solved! with a orange background. If the date on the computer is set to a date between 03/20/2018 and 06/21/2018, you should see the message Spring is here! *Call us* now before your Lawn Paynes are out of control! with a red background. If the date is set past 06/21/2018, there will be no message.

2. `nameValidate()`, `emailValidate()`, `phoneValidate()`, `commentValidate()` file: [lawn_form.js](https://github.com/ryansallee/ryansallee.github.io/blob/master/js/lawn_form.js) Page: [Contact](https://ryansallee.github.io/contact.html)
- All four of these functions are called when the click event on the submit button (`submitButton`) occurs. These four functions validate their inputs to ensure the input fields for name, email, phone number, or comments is not blank by using the `.val()` method. As well the `emailValidate()` and `phoneValidate()` validate their respective inputs against regex values for email and phone that are stored in `emailFormat` and `phoneFormat` by using the `.test()` method against their respective inputs. If the inputs are blank or do not match a valid email or phone number format, each function sets their respective variables (`doNotSubmitName`, `doNotSubmitEmail`, `doNotSubmitPhone`, `doNotSubmitEmail`), to true, and a message is inserted in a div below each respective input advising information is needed or invalid.   If any of the four variables `doNotSubmitName`, `doNotSubmitEmail`, `doNotSubmitPhone`, or `doNotSubmitEmail` are true, an error is thrown and will be shown in the console and the code for the click event will not execute any further to the `$.ajax` function.
- Testing Notes: To test the validations, please leave any combination of the inputs on the Contact page blank, enter a phone number in an invalid North American phone number format, or an email in an invalid format such as just a single letter or an email with out a domain. If any of these invalid inputs are submitted, messages advising input is needed or invalid will display below their respective inputs.

3. `$.ajax` file: [lawn_form.js](https://github.com/ryansallee/ryansallee.github.io/blob/master/js/lawn_form.js) Page: [Contact](https://ryansallee.github.io/contact.html) 
- The jQuery `$.ajax` function is executed if the the validations `nameValidate()`, `emailValidate()`, `phoneValidate()`, `commentValidate()` are sucessful (`doNotSubmitName`, `doNotSubmitEmail`, `doNotSubmitPhone`, `doNotSubmitEmail` are all false) after the click event on the submit button(`submitButton`). The AJAX request is configured as a POST request, with the the serialized data from the inputs in the form (`formData`), and sends the request to a URL that returns a response with a CORS (Cross-Origin Resource Sharing) header that bypasses the same-origin policy. If a successful response is sent, a function is called to fade out the form using the `.fadeOut()` jQuery method and an anonymous function is called to fade the form back in using `.fadeIn()` and display `successMessage` in the form. If the response is an error, the `.errorAlert` class is selected and `errorMessage` displays in this div above the Name input.
- Testing Notes: To test the form, please place valid input in the input fields and submit the form. The form will fade out over 1 second, and the message contained in `successMessage` will fade  in over 1 second. To test the error message, load the page, disconnect from your web connection, and then submit the form. Since the there will be no request, an error will be returned for the request and `errorMessage` will display in the div above the Name input.

4. `slideShow(n)`, `showButtons()`, `slidemove(n)`, `stop()`, `resume()` file: [lawn_slide_show.js](https://github.com/ryansallee/ryansallee.github.io/blob/master/js/lawn_slide_show.js) Page: [Our Work](https://ryansallee.github.io/our_work.html)
- These 5 functions establish an automatic slide show with Previous, Pause, Next, and Stop buttons to allow a user to have control over the slide show. 
    1. `slideShow(n)` is executed upon page load since the `<script>` tags are placed at the end of the HTML file of [Our Work](https://ryansallee.github.io/our_work.html). This function starts by ensuring that the parameter n is defined with a condition as the function is called in `slideInterval` every 3 seconds with n undefined and advances `slideNumber` by 1 with the increment operator; this will be index number of the slide to be displayed in `slides`. As well, conditions are used to make sure that n does not exceed the final index (3) or the first index (0) of `slides` as this would create an error. Nextly, a for loop is used to hide the current slide by setting its display to none displayed as `i` will always be one behind the value of `slideInterval`. The next slide will display by setting the index of `slides` determined by the value of `slideInterval`  

## CSS Classes
1. `.slide-container` file: [our_workstyle.css](https://github.com/ryansallee/ryansallee.github.io/blob/master/css/our_workstyle.css) Page: [Our Work](https://ryansallee.github.io/our_work.html)
- The purpose of this this custom class is to set a flex container for the images displayed on small screens to stack them upon one another as well as set a limiting container the images in the slideshow on larger screens (>=640px). For all screens, this container gives depth to the page with a box-shadow style and decreases the blockiness of the container with a border-radius style of 25px in addition to providing some contrast by using a shade of blue, but with the gradient-direction reversed from the direction of the body.On smaller screens, the container almost fills the page with a 97.5% width to give it some breathing room, but ensure that the container is not small on mobile devices. For larger screens, the width is decreased so that the `.slides` container that contains slideshow images are not overly large, and padding is applied to allow the `.slides` container to breathe since the img selector for tablet sized screens fills the whole `.slides` container with a 100% max-width and max-height. Furthermore, the width is significantly decreased on desktops and laptops (>=1025px)to ensure that the container does not extend below the user's viewport.

2. `.contactForm` file: [contact.css](https://github.com/ryansallee/ryansallee.github.io/blob/master/css/contact.css)
Page: [Contact](https://ryansallee.github.io/contact.html)
- To set up a flex container for the contact form so that all of the inputs are stacked upon one another, I created this custom CSS class. This class as well provides contrast to the background color of the body with a white background-color style. Like the `.slide-container` class, depth is given the to the page with a box-shadow style. As well, the base style gives it a 97.5% width for the container on small screens for maximum visibility with some breathing room of the background, since the base styles are mobile-first. Furthermore, the width decreases on the breakpoints for tablets (>=640px) and laptop and desktop screens (>=1025px) where the width is equivalent to the `.main-header` class to make sure that the edge of the `.contactForm` is aligned to the navigation and title in the header for a clean look. As well the `contactForm` gives a top margin +10px of the height of the header due to the header's use of fixed positioning for a stickyheader. For balance, a bottom margin of 10px is applied as well. 

3. `.slides` files: [our_workstyle.css](https://github.com/ryansallee/ryansallee.github.io/blob/master/css/our_workstyle.css) & [our_work_no_script.css](https://github.com/ryansallee/ryansallee.github.io/blob/master/css/our_work_no_script.css) Page: [Our Work](https://ryansallee.github.io/our_work.html)
- This custom selector contains each of the images as well as their captions. For the slideshow that runs on devices with a viewport greater than or equal to 640px, the `.slides` selector uses the nth-of-type selector to hide the second `.slides` container and every `.slides` container therafter as nth-of-type is set to 1n+2. If JavaScript is disabled by a visitor, the [our_work_no_script.css](https://github.com/ryansallee/ryansallee.github.io/blob/master/css/our_work_no_script.css) file embedded in `<noscript>` tags reverses `.slides` containers 2-4 being set to none by setting them back to block.
- Testing Notes: Please disable JavaScript on a device with a viewport greater than or equal to 640px such as a tablet or laptop, and all of the the images that play on the auto-slide show will appear stacked upon one another.

## Additional Testing Notes:
1. `<noscript><p>... ` file: [contact.html](https://github.com/ryansallee/ryansallee.github.io/blob/master/contact.html) Page: [Contact](https://ryansallee.github.io/contact.html) 
- This tag contains a message to advise a vistor that the form will not function when JavaScript is disabled. The prrevious `<p>` tag and its message is hidden by the CSS selector p:nth-child(2) in [contact_no_script.css](https://github.com/ryansallee/ryansallee.github.io/blob/master/css/contact_no_script.css). Please disable JavaScript and then reload the page to test that the message in the `<p>` tag that is nested in `<noscript>` displays rather than the previous `<p>` tag.
