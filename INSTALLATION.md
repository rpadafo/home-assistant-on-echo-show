# Installation

1. In Home Assistant, go to Configuration > Dashboards and press the "Add Dashboard" button. <div align="center"><img src="img/add_dashboard.jpg" /></div

2. Choose "New dashboard from Scratch" (or your favorite option). Choose a name and the URL for the dashboard. Remember the "Dashboard URL" if you want to add to the URL later. <div align="center"><img src="img/dashboard_creation.jpg" /></div>

3. Open the dashboard (click on "open"), click on "Edit Dashboard" in the top right corner.

4. Edit the view "Home" if you want.<div align="center"><img src="img/edit_home.png" /></div>

5. You can now create your view as you like. Remember to adjust the elements according to the screen you are going to use.

6. Now we're finished in Home Assistant. Open the [Alexa Developer Console](https://developer.amazon.com/alexa/console/ask) and sign-in with the Amazon account that is linked to your Echo Show.

7. I recommend switching the language of the Alexa Developer Console to "English (US)" in the bottom left corner. This will make following these instructions much easier.<div align="center"><img src="img/locale.png" /></div>

7. Click on "Create Skill".<div align="center"><img src="img/create_skill.png" /></div>

8. Enter a skill name (I chose "Dashboard Viewer") and make sure that the correct locale is selected (the language you use for your Echo Show). For the model select "Custom" and for the backend select "Alexa-hosted (Python)".

9. In the top right corner adjust the hosting region to something that is close to you and press "Create skill" <div align="center"><img src="img/create_skill_2.png" /></div>

10. On the next page make sure "Start from Scratch" is selected and press "Continue with template".

11. You should now be on this page. <div align="center"><img src="img/menu.png" /></div>

12. In the menu on the left select "Invocations" > "Skill Invocation Name". Here you can set the name of your skill. You will use this name to call the skill. We will use "dashboard viewer", however, if the language of your Alexa device differs from English it might be useful to choose something in your language (Alexa might not understand it otherwise). <div align="center"><img src="img/invocation.png" /></div>

13. Again in the left menu select "Interaction Model" > "Intents". Delete the ``HelloWorldIntent``, we won't need it. Click on the "Add Intent" button. Select "Create custom intent" and choose ``OpenPageIntent`` as its name. Press on "Create custom intent" afterwards.<div align="center"><img src="img/open_page_intent.png" /></div>

14. On the next page first scroll down to "Intent Slots". Use ``page`` as the name for the slot and click on "+" to add it. As "Slot Type" select ``AMAZON.NUMBER``. <div align="center"><img src="img/intent_slots.png" /></div>

15. Then scroll up to "Sample Utterances". Here you can choose the command that is used to call the skill. We will use `open page {page}`. The ``{page}`` is a placeholder for a number which will later be used to open the respective view of the dashboard. You add the "utterance" by clicking on the "+" on the right. Again, if the language of your Alexa device differs from English you should choose a command in your language. The only important thing is that you use the placeholder ``{page}`` appropriately. It should be highlighted if everything is correct. <div align="center"><img src="img/sample_utterance.png" /></div>

16. On the top click "Save Model". <div align="center"><img src="img/save_build_model.png" /></div>

17. Again in the left menu navigate to "Interfaces". Activate the option "Alexa Presentation Language".<div align="center"><img src="img/interfaces.png" /></div>

18. Click on "Save Interfaces". Then click "Build Model".<div align="center"><img src="img/save_interfaces.png" /></div>

19. Wait until you get the notification "Build Completed". Afterwards navigate to the Code tab.<div align="center"><img src="img/code_tab.png" /></div>

20. In the code editor replace the content of the ``lambda_function.py`` file with the content of the ``lambda_function.py`` file from this repository. It can be found [here](lambda_function.py). Change the ``DASHBOARD_URL`` variable according to step 1: We chose ``echo-show`` as URL in the first step. Assuming our Home Assistant URL is ``https://homeassistant.local:8123``, the ``DASHBOARD_URL`` should be ``https://homeassistant.local:8123/echo-show/``. I use [Kiosk Mode](https://github.com/maykar/kiosk-mode) to hide the header and sidebar drawer from Home Assistant. If you have [Kiosk Mode](https://github.com/maykar/kiosk-mode) installed you can use the ``KIOSK_MODE`` variable to enable/disable Kiosk mode. If you don't have [Kiosk Mode](https://github.com/maykar/kiosk-mode) installed, this option won't have any effect, therefore you can set it to ``False``. When you are finished, click on "Save". <div align="center"><img src="img/dashboard_url.png" /></div>

21. Right-click on the ``lambda`` folder and select "Create File". <div align="center"><img src="img/create_file.png" /></div>

22. Select ``lambda/template.json`` as file path. <div align="center"><img src="img/template_json.png" /></div>

23. Paste the contents of the ``template.json`` from this repository (which can be found [here](template.json)) into the newly created ``template.json`` file. <div align="center"><img src="img/paste.png" /></div>

24. Click on "Save" and on the "Deploy" button. Wait until you get the notification "Deployment Successful". <div align="center"><img src="img/save_deploy.png" /></div>

25. Navigate to the "Test" tab. <div align="center"><img src="img/test_tab.png" /></div>

26. Select "Skill testing is enabled in: Development" from the dropdown and you are done 🎉. <div align="center"><img src="img/skill_testing.png" /></div>

27. You can test the skill by opening it on your Alexa device. Since we chose ``dashboard viewer`` as the invocation name, we would open the skill by saying ``Alexa, open dashboard viewer``. This should open the default view of the dashboard. If you never signed in to your Home Assistant account on your Echo Show, you might need to do this then. Make sure to select the "keep me logged in" option because you don't want to this every time you open this skill. When this works, you can test out if the view selection works. According to our utterance from step 14 we would need to say ``Alexa, tell dashboard viewer open page <number>``, where ``<number>`` is the URL of the view you want to open. Of course, you would need to create such a view first; this is described in step 4.
