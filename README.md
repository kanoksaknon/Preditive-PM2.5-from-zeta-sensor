#Ai-Model
#ใช้ KNN MODEL

#KNN MODEL คืออะไร
#K-Nearest Neighbors (KNN) เป็นอัลกอริทึมการเรียนรู้แบบมีผู้ดูแลที่ใช้ความใกล้ชิดเพื่อจัดประเภทหรือทำนายการจัดกลุ่มของจุดข้อมูลใหม่
#อัลกอริทึมนี้ทำงาน ดังนี้
#1.เลือกค่า K: เลือกจำนวน "เพื่อนบ้าน" ที่ใกล้ที่สุดที่ต้องการพิจารณา
#2.คำนวณระยะทาง: คำนวณระยะทางระหว่างจุดข้อมูลใหม่และจุดข้อมูลทั้งหมดในชุดข้อมูลการฝึกอบรม
#3.ระบุเพื่อนบ้านที่ใกล้ที่สุด: ระบุจุดข้อมูล K ใกลที่สุดจากขั้นตอนที่ 2
#4.ทำนาย: ทำนายคลาสหรือค่าของจุดข้อมูลใหม่ตามคลาสหรือค่าเฉลี่ยของเพื่อนบ้านที่ใกล้ที่สุด

#ทำไมProject นี้ผมถึงเลือกใช้ KNN MODEL
#โมเดล KNN (K-Nearest Neighbor) เป็นหนึ่งในอัลกอริทึมการเรียนรู้ของเครื่องที่มีประสิทธิภาพและใช้งานง่าย เหมาะอย่างยิ่งสำหรับการพยากรณ์ค่า PM2.5
#เหตุผลหลักๆ ที่เลือกใช้ KNN 
#1. ความแม่นยำ: KNN พิสูจน์แล้วว่ามีประสิทธิภาพสูงในการพยากรณ์ค่า PM2.5 ผลงานวิจัยหลายชิ้นเปรียบเทียบโมเดล KNN กับโมเดลอื่นๆ พบว่า KNN มักให้ผลลัพธ์ที่แม่นยำกว่า
#2. ความยืดหยุ่น: KNN สามารถปรับให้เข้ากับข้อมูลประเภทต่างๆ รองรับทั้งข้อมูลเชิงตัวเลข ข้อความ และรูปภาพ โมเดลนี้ไม่มีสมมติฐานที่ซับซ้อน ทำงานได้ดีกับข้อมูลที่ไม่เป็นเส้นตรง
#3. ความง่ายต่อการใช้งาน: KNN มีหลักการทำงานที่เข้าใจง่าย ไม่จำเป็นต้องมีความรู้ด้านสถิติหรือคณิตศาสตร์เชิงลึก เหมาะสำหรับนักวิจัย นักวิเคราะห์ข้อมูล และนักพัฒนาซอฟต์แวร์ทุกระดับ
#4. ประสิทธิภาพ: KNN ทำงานได้รวดเร็ว เหมาะสำหรับการวิเคราะห์ข้อมูลขนาดใหญ่
#5. การเรียนรู้จากข้อมูลใหม่: KNN สามารถเรียนรู้จากข้อมูลใหม่ได้อย่างต่อเนื่อง โมเดลจะปรับปรุงประสิทธิภาพการพยากรณ์เมื่อมีข้อมูลใหม่อัปเดต

#จากนั้นก่อนนำเข้าโมเดลจึงเช็คData ที่มีซึ่งปรากฎว่าต้องทำการคลีน Data ก่อน
![101Zeta](https://github.com/kanoksaknon/Preditive-PM2.5-from-zeta-sensor/assets/163635486/223011b4-28e4-4568-b9d1-1e2b1d63d329)
# จะสังเกตุว่า Data ยังไม่ถูก Clean และแยกส่วนกัน รวมถึงมีหลายส่วนที่ไม่ได้ใช้ (เราจะใช้แค่ส่วนของข้อมูลของ วันที่ แล้วก็ค่าของเซนเซอร์ในแต่ละตัวเท่านั้น)ในที่นี้ผมจะใช้ Excel ในการคลีนData

#ขั้นแรก :  เราจะทำการลบในส่วนที่เราไม่ได้ใช้ทิ้งไป ประกอบไปด้วย Data type, Asset, number, Asset name, System, Install location, Device type, Device ID, Project
#หลังทำการลบจะได้แบบนี้
![After](https://github.com/kanoksaknon/Preditive-PM2.5-from-zeta-sensor/assets/163635486/e3781f14-0979-4c38-85dc-1c9f25b36dca)

#ขั้นสอง :  เราจะทำการแยกแถวใน Content โดยใช้ Text to Column
![1](https://github.com/kanoksaknon/Preditive-PM2.5-from-zeta-sensor/assets/163635486/66540828-2700-4328-b9b5-1ac4be1649d1)
![2](https://github.com/kanoksaknon/Preditive-PM2.5-from-zeta-sensor/assets/163635486/96471371-093f-4d6c-86ea-8cad3eb2677b)
![3](https://github.com/kanoksaknon/Preditive-PM2.5-from-zeta-sensor/assets/163635486/02fec3a7-dfe8-4a2a-ab8b-fe1715e11c39)
#ผลลัพธ์ที่ได้หลังแยกdata ใน Content
![After2](https://github.com/kanoksaknon/Preditive-PM2.5-from-zeta-sensor/assets/163635486/5cace752-92de-45b5-bf30-569ed14a4e1b)

#ขั้นสาม : ทำการลบในส่วนของ ที่เกินมาและไม่ได้ใช้ หลังจากนั้น นำมาจัดใหม่ให้สวยงาม พร้อมใช้
![After3](https://github.com/kanoksaknon/Preditive-PM2.5-from-zeta-sensor/assets/163635486/c722ef12-5a91-4dee-8a0c-42836472514b)

#ขั้นสุดท้าย : ทำการเคลียร์หน่วยในช่องทุกตัวเนื่องจากว่า ตอนจะนำเข้าโมเดลนั้นจำเป็นต้องไม่มีหน่วยอยู่ในช่อง
![After4](https://github.com/kanoksaknon/Preditive-PM2.5-from-zeta-sensor/assets/163635486/d88d7f0b-a639-419b-8dac-f20cd581a5ea)

#จากนั้นเราก็ไปดูในส่วนของไฟล์ 495_KNN_SUCESS.ipynb ในการนำข้อมูลเข้าและเทรนโมเดลได้เลยครับ
https://github.com/kanoksaknon/Preditive-PM2.5-from-zeta-sensor/blob/main/495_KNN_SUCESS.ipynb



