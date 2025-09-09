---
title: "The Cardiac Phantom"
excerpt: "An anatomically accurate and pulsatile pediatric phantom for Cardiac MRI Training <br/><img src='/images/500x300.png'>"
collection: portfolio
---

![Image of requirements](/images/img2.jpg)

Sponsored by the Digital Lab (link), an organization that works in collaboration with Doctors at BC Children's Hospital, I set out to develop an anatomically accurate and pulsatile pediatric cardiac phantom for Cardiac MRI Training. The overarching goal of this project is to create a fabrication pipeline for pediatric cardiac pathologies, such as Congenital Heart Defects, to help train technicians and radiologists in identifying these abnormalities. The main requirements of the project are illustrated above. 

![Image of requirements](/images/img3.jpg)

Past research suggests that Silicones with a Shore hardness between 0A and 10A provide realistic tissue properties. However, 3D printers that print in this range can be costly, in the range of $10k-$100k, which is well over the project budget. Instead, I followed the following paper (link) and adjusted along the way to cast a Silicone 00-30 pediatric heart in 42 hours. This cost of this process amounts to about $250-$500 depending on anatomy, given that there is a 3D printer available to use. This process is a modified lost-wax molding process shown above. The aim of the process is to create a dissolvable inner mold out of wax which can be melted out to retain an accurate interior anatomy. This process can also be conducted with Silicones of greater hardness and with different pathologies.

![Image of requirements](/images/img4.jpg)

First, the 3D model of the heart was imported into Meshmixer to create the molds. The 5 major blood vessels (inferior vena cava, superior vena cava, pulmonary artery, pulmonary vein, aorta) were marked and additional blood vessels were removed. The wax mold and the exterior mold were created using Boolean subtraction and were sliced to create a multipart mold to ensure mold removal with minimal damage. The wax mold was sliced into 38 pieces due to the delicate nature of wax, and the exterior mold was sliced into 10 pieces. Alignment sections were added into both molds. 

Both molds were 3D printed in PLA using a BambuLabs X1 Carbon. After assembling the wax mold, a wireframe was placed inside the mold, the wax was poured in, and the mold was then placed in a freezer for 4 hours to set. A planned and careful approach towards mold removal was taken to minimize cracks. The wireframe helped maintain position of broken pieces - resulting in a simple fix using a soldering iron. The interior mold was placed in the exterior mold, and the Silicone 00-30 was poured into the mold and cured. After four hours, the exterior mold was removed and the interior mold was melted out, leaving a silicone heart.

![Image of requirements](/images/img5.jpg)

Overall, the process required 12 hours of hands-on work out of the 42 hours. In addition, it can be planned as shown below to be completed in 3 days depending on resources.

![Image of requirements](/images/img6.jpg)

The heart was assembled in a rigid holder with two molded Silicone 00-30 ballons to pulse the left and right ventricles. The pulsing was controlled by an Arduino which controlled an electropneumatic to switched between compressed air and atmospheric pressure. A clamp was added to the pulmonary artery/vein and the right ventricle was actuated to measure the ejection fraction. The results are shown in the graph below. The main limitation towards reaching the normal range for left ventricle ejection fraction and heart rate was the actuator design. In the future, the actuators can be improved upon similar to the Roche lab (link) to achieve more realistic pulsing characteristics. Additionally, actuators for the atriums can also be added.

![Image of requirements](/images/img7.jpg)

The cardiac phantom was then imaged at the UBC MRI Research Facility using the 9.4 Tesla pre-clinical MRI. Some of the results are shown below. The heart was pulsing at 60 BPM at 30 psi as they provided the closest ejection fraction to normal pumping. Overall, the cardiac phantom successfully demonstrated pumping motion, close resemblance to interior anatomy of model, and MRI compatibility.

A special thanks for all the help and support from the staff at the UBC Engineering Physics Project Lab, the Digital Lab, and the UBC MRI Research Center.


