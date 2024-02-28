单纯只是想证明我尝试过，它运行不起来

	#include<bits/stdc++.h>
	#include <iostream>
	#include <cmath>
	using namespace std;
	#include <Eigen/Core>
	#include <Eigen/Geometry>
	using namespace Eigen;
	int main(int argc, char **argv) {
    	 double x,y,z,h,lX,lY,X,Y;
 		scanf("%lf%lf%lf%lf%lf%lf",x,y,z,h,lX,lY);
 	 	AngleAxisd rotation_vector(-z, Vector3d(0, 0, 1));
     	Matrix<double, 3, 3> intrinsics;
     	intrinsics << 1,2,3;4,5,6;7,8,9;//2
     	Matrix<double, 3, 1> vd_3d;
     	vd_3d << x,y,1;
     	Matrix<double, 3, 1> result = intrinsics.inverse() * vd_3d*h;
    	 Vector3d result_rotated = rotation_vector * result;
    	 X=result_rotated(0,1)/20000000*360+lX;//1
    	 Y=result_rotated(0,2)/20000000*360+lY;
     	cout << "location is"<<X,Y;
    	 return 0;
	}