四元數的3D運算

p點為y軸上的一點P(1,0,0)，對Y軸a角度旋轉，a為90度，其運算過程

p'= qpq*

p'為運算後的結果

q為旋轉四元數

q*為旋轉四元數的共軛conjugate

q = (s, ix, jy, kz )
s 為 scale ，其他i,j,k都是複數空間

q = (cos(a/2), sin(a/2)*x, sin(a/2)*y, sin(a/2)*z)

其中只對Y軸(0,1,0)進行旋轉 所以 

q = (0.707, 0.707*0, 0.707*1, 0.707*0)
q = (0.707, 0, 0.707, 0)
q'= (0.707, 0,-0.707, 0)

參考
http://math.stackexchange.com/questions/40164/how-do-you-rotate-a-vector-by-a-unit-quaternion
http://www.euclideanspace.com/maths/geometry/rotations/conversions/angleToQuaternion/

四元數運算 Hamilton product
https://en.wikipedia.org/wiki/Quaternion#Hamilton_product
    
    q = [0.707,		0,		0.707,		0]
    p = [0,			1, 		0, 			0]
    q'= [0.707,		0, 		-0.707,		0]
    
    
    H(q, p) = [0.0, 0.707, 0.0, -0.707]
    H(H(q, p), q') = [0.0, 0.0, 0.0, -1]
    
    q =[s1, x1, y1, z1]
    p =[s2, x2, y2, z2]
    H(q, p)=
    [ 
    s1*s2 - x1*x2 - y1*y2 - z1*z2
    ,
    s1*x2 + x1*s2 + y1*z2 - z1*y2
    ,
    s1*y2 - x1*z2 + y1*s2 + z1*x2
    ,
    s1*z2 + x1*y2 - y1*x2 + z1*z2
    ]

	注意這裡的表示方式應該是 s,i,j,k 但是為了對應 點的表示方式，所以寫成 s,x,y,z。    






之所以要這樣做乘法是因為 無法像 Eular 空間那樣，乘以一個點就能完成旋轉，必須分成兩次所以公式中的 a 角度必須除以2。

q 跟 q'都會旋轉一樣的角度，所以兩者合就是原本要旋轉的角度，如此一來才能維持一樣的向量長度。


最重要的參考
http://www.songho.ca/math/quaternion/quaternion.html