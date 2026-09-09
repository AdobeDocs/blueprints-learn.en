---
title: Create Decision Rule
description: Build a Decisioning Rule that restricts eligibility for premium phone offers to customers on higher-tier plans.
doc-type: article
solution: Experience Platform
exl-id: 1c1e2d82-ca09-4074-813d-3b29af77388b
---

# Create Decision Rule

## Objective

Since eligibility is one of the key building blocks of an offer, the first step is to create the necessary entities to support it. In many cases, audience membership is the deciding factor, but in this case, we'll use Decision Rules. With Connection 5G, higher-end iPhone 17s can only be activated for users with a high-tier plan. As such, we'll use a decision rule to ensure that offers for higher-end phones are available only to those with a high enough plan. 

## Create the Decision Rule

1. If necessary, log in to the Adobe Experience Cloud and navigate to **Adobe Journey Optimizer.**
2. Expand the **Decisioning** menu item in the left rail if necessary, and click on **Strategy Setup.**

>[!WARNING]
>
>Be sure you are in the Decisioning menu and NOT the Decision Management menu. If the Decision Management menu is expanded, collapse it to avoid navigation confusion during this lab.

3. Click on **Decisioning Rules** under the 'Eligibility' menu, followed by the **Create rule** button in the upper right corner.

![Navigating to Decision Rules](assets/create-decision-rule-1.png)

4. You will be taken to a screen that resembles the Segment Builder UI. Add the Plan ID attribute to the rule canvas by clicking on **XDM Individual Profile > DEP > Plan Details** and then dragging the **Plan ID** attribute to the canvas.
5. Change the drop-down from equals to **contains.**
6. Enter the text **2** in the box, press **Tab** key to accept the 2 value, then enter a **3,** press **Tab** again so that the rule is looking for any Plan IDs that contain a 2 or 3
7. Use the **Name** textbox in the right rail to name the Decision Rule **Upper Tier Plans**. Add a description if you'd like. When finished, your Decision Rule should look like this:

![W1YLuDeRos8EcyCAq1Oh2 20251202 203901.png "Decision rule finished state"](assets/w1YLuDeRos8EcyCAq1Oh2-20251202-203901.png "Decision rule finished state")

8. Once the rule is correct, click the blue **Create** button in the upper-right corner, and you'll be returned to the Strategy Setup page with the Decision Rule you just created listed as the only Decision rule.

>[!NOTE]
>
>Why use a Decision Rule instead of an Audience? In practice, the primary reasons would be that you needed eligibility criteria specific to the decisioning package or you needed attributes of the offers in the criteria. Offer attributes aren't available fields in the Audience builder. 
>
>The Upper Tier Plans Decisioning Rule used in this lab would likely be an actual Audience in a real-life implementation, given its likely re-usability outside of Decisioning. However, a Decisioning Rule was used here for educational purposes and to showcase its functionality and the multiple ways eligibility can be applied. 

## Recap

You've now created a reusable Decision Rule, which you will use for offer eligibility.
