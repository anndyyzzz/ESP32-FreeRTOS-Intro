# การทดลอง ESP32 FreeRTOS 
##  ฟังก์ชัน vTaskDelete()

1. แก่ไข Code จากโปรแกรมที่แล้ว โดยการเพิ่ม task เข้าไปอีก 1 task

```c
...

void My_First_Task(void * arg)
{
	uint16_t i = 0;
	while(1)
	{
		printf("Hello My First Task %d\n",i);
		vTaskDelay(1000/portTICK_PERIOD_MS);
		i++;

		if(i == 5)
		{
			vTaskDelete(MySecondTaskHandle);
			printf("Second Task deleted\n");
		}
	}
}

...
```

จากโปรแกรมด้านบน เมื่อมีการนับจน i == 5 จะทำให้เงื่อนไขในประโยค if เป็นจริง

คำสั่ง `vTaskDelete(MySecondTaskHandle);` จะลบ `MySecondTaskHandle` ออกจาก list ของ task ที่จะทำงาน


4. รันและบันทึกผลจากโปรแกรมข้างบน วิเคราะห์ผลที่ได้ว่าเป็นอย่างไร
![Screenshot 2024-10-30 133455](https://github.com/user-attachments/assets/ed315220-a58e-4c37-8f52-8568fac961b6)

### พอ Hello My First Task ถึงเลข 5 Hello My Second Task จะถูกลบออก

## [>> ต่อไป >>](./ESP32-FreeRTOS-Labsheet-5.md) 
