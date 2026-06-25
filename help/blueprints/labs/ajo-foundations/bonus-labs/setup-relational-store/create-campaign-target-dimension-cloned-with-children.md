---
hold: true
title: Create Campaign Target Dimension (cloned with children)
description: Create Campaign Target Dimension (cloned with children)
doc-type: article

solution: Experience Platform
exl-id: 957bfbe4-42c1-45fe-824e-11106ccc4b6b
---

This lab will cover configuring the Profile Target Dimension for the Relational schema created in the previous step.

The Profile Target Dimension in a relational schema is a configuration that enables targeting communications at the entity level. It leverages the relational schema capabilities of Adobe Experience Platform to define which schemas are eligible for targeting and how they are linked to the Real-Time Customer Profile schema.

# Configure Campaign Target Dimension

1. Click on the **Apps** icon and select **Journey Optimizer**

![K3Q7jr7t5wanoprIui7sf 20251208 042621](assets/K3Q7jr7t5wanoprIui7sf-20251208-042621.png)

1. Click on **Configurations** under **Administration**

![IlchseyC096oQQNdaNVSc 20251208 205011](assets/IlchseyC096oQQNdaNVSc-20251208-205011.png)

1. Select **Profile Target Dimension** and click on **Manage**

![JQOW0f5EqcFeEl5pIpIDF 20251208 205010](assets/jQOW0f5EqcFeEl5pIpIDF-20251208-205010.png)

1. The Profile Target Dimension pane opens, click on **Create**

![OVUuHyNWa9 20251208 205010](assets/BEuyDbO9H5_OVUuHyNWa9-20251208-205010.png)

1. In the Create Profile Target Dimension section, select the recently created `oc_mdl_customer` schema from the drop down

![AfLKopsR 20251208 205010](assets/ygdCtgQFe22f_afLKopsR-20251208-205010.png)

1. For **Identity value** select the primary key, `customer_id`, for the `oc_mdl_customer` schema 

![Ao6qbcEgXclf6q0nanQ34 20251208 205010](assets/Ao6qbcEgXclf6q0nanQ34-20251208-205010.png)

1. Click on **Save**

![9atydrwtvRfv79j0aexl1 20251208 205010](assets/9atydrwtvRfv79j0aexl1-20251208-205010.png)

1. Wait for the confirmation message, the **Profile Target Dimension** for the `oc_mdl_customer` schema has been created

![3AtDPonYl5woQkkKK450C 20251208 205010](assets/3AtDPonYl5woQkkKK450C-20251208-205010.png)

>[!TIP]
>
>The Profile Target Dimension has been created and will be used in the next lab.
>
>Congratulations! this concludes the Profile Target Dimension creation step in the lab.

## Reference

[https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/data-configuration/target-dimension](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/data-configuration/target-dimension)
