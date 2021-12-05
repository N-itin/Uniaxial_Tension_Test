# Uniaxial_Tension_Test
A program, which evaluates Hooke’s law for the case of a uniaxial tension test with a sinusoidal time series.
This program provides evaluation of Hooke’s law for the case of a uniaxial tension test with a sinusoidal time series. Python is chosen for its user-friendly interface, easy coding, editing and provides a great number of libraries which can be used to interact with external software also.

	The user should specify the parameters of the test course as well as Hooke's law via a text file - 'D:/input_format.txt'
	The components of the resulting stress state shall be displayed graphically over time as well as the deformation – section 1.3 
	The results of the evaluation of the material law shall be written into a text file. The file name as well as the location shall be defined by the user.
	Geometry of the specimen is described as per technical standards (ASTM, DIN, ISO.)
	The general procedure of the test is described below - section 1.1
	Explanation of the calculation of stresses and strains in section 1.2

1.1 General procedure (some aspects): 
	Preparation 
	Get initial cross-sectional area of test specimen 
Set initial length for extensometer 
Mount specimen inside the clamps 
	Upon start of the test program: 
Extensometer arms are attached 
Loading program is started 
	Extensometer-arms follow the elongation of the specimen 
	Force is measured by the load cell 
	At the end of the test program: 
Graphical review 
Export of data for further processing 

The specimen (dumbbell shape) at the top and bottom is clamped in the universal testing machine (UTM). We chose a region of homogeneous strain state into the specimen between the clamping region (Figure 1), this will be the measuring region for the experiment. This region a little away from clamping region because the strain appears little bit differently in both the clamping and homogeneous strain state region. Measuring system is attached to specimen which measures the stretches or strains inside the measuring region only
In Figure 1, a dumb bell-shaped specimen is shown.

L(t) is the length of the measuring region which is a 
region of homogeneous strain state. 
F(t) – Force applied in uniaxial direction.
u(t) = displacement of the specimen in x direction
           due the application of force F(t).
Figure 1


Section 1.2
Basically, we can measure the cross-sectional area of the test specimen in the region homogeneous strain state at the beginning of test and then with application of the force during the experiment, the 1st Piola Kirchoff stress, T (or engineering stress) can be easily measured. If we can measure the lateral stretch and current cross-sectional area at any time (t) then true stress, σ (or Cauchy stress) can also be measured. But the cost of measuring systems and accuracy of measurement of lateral stretches can only be justified from case-to-case basis and availability of resources. However, we can calculate the Cauchy stress from 1st Piola Kirchoff stress, poison’s ratio and volume ratio.
Poisson’s ratio, ν, defined as the ratio of the lateral contraction to the elongation, is of particular interest for materials near the glass transition since ν may exhibit a time or frequency dependence. Mathematically, when ν = 1/2 the ratio of the bulk to shear modulus K/G is infinite and the system is described as incompressible. Experimentally, all materials are compressible (i.e., K is finite), and while the Poisson’s ratio can approach 1/2, it never actually equals 1/2. In viscoelastic materials, when ν is close to 1/2, G << K and the material is commonly called ‘‘incompressible’’.
The measurement of initial length, width, thickness and cross-sectional area at the beginning of experiment (at time t = 0 s) for uniaxial tension test will be done.
In the elastic deformation range of materials, the methods of calculating the material stresses from the measured strains are based on Hooke's Law. In its simplest case of unidirectional loading form Hooke's Law is:
T (t) = εxx (t) * Ε      
T(t) = 1st Piola Kirchoff stress (or engineering stress) [N/mm2]
εxx (t) = strain in loading direction [mm/mm]
Ε = modulus of elasticity, i.e. Young’s modulus [N/mm2]
  
In the region of homogenous strain state at beginning of the experiment and initial time, to
	Length of the specimen in the region of homogenous statin state (or measuring region) is denoted by L mm. Initial Length is measured at the start of the experiment and is denoted by L(to) mm. This length is also set for the extensometer.
	Width of the specimen in the region of homogenous statin state (or measuring region) is denoted by W mm. Initial width is measured at the start of the experiment and is denoted by Wo (at t = to) mm.
	Thickness of the specimen in the region of homogenous statin state (or measuring region) is denoted by S mm. Initial thickness is measured at the start of the experiment and is denoted by So (at t = to) mm.

Therefore, cross sectional area can be calculated from above parameters:

	Ao = Wo * So mm2





Loading program:
A sinusoidal loading program is applied to the specimen, with Force, F [N]:
F (t) = Fo sin (ωt) [N], where	Fo= amplitude of the force applied 
ω = angular velocity (radian per second) [ to be defined in program as constant] as this will be same as the speed of the crosshead transverse motion of UTM which is also constant for the experiment.
t = time in seconds [s] for the which force is applied.
With the application of the force, the specimen elongates in the measuring region, this stretch is recorded with help of extensometer sensor and the file is saved in .txt format which serves as the input file to the program. 
The .txt file (input file for the program) contains following data:
  # time [s]   length [mm]  force [N]
Calculations:
	Calculation of stress from Measurement data.
Engineering stress (1st PK): T(t) = F(t)/Ao 
F(t) = Fo sin (ωt) [N],
Ao  = initial Cross sectional area at the beginning of the test for the measuring region. 
	Calculation of strain from Measurement data.
Stretch ratio in loading direction: λ(t) = L(t)/L(to) 
L(t) = current length of measuring region at time t (s).
L(to) = initial length of measuring region at the beginning of the test at time to (s).
We can calculate the engineering strain and true strain after the measurement of the stretches in longitudinal direction and calculation of lateral strain with help of poison’s ratio. 
Engineering strain:
	In longitudinal direction, Linear εxx (t) = \frac{\mathbit{L}(\mathbit{t})}{\mathbf{L}(\mathbf{to})}-\mathbf{1} = λ(t) – 1 where λ(t) = stretch ratio in longitudinal direction during uniaxial tension. 
	In lateral directions, Linear εyy (t) and εzz (t) = - ν εxx (t)

Engineering Stress state 
[T(t)] = [ \begin{matrix}T(t)&0&0\\0&0&0\\0&0&0\\\end{matrix}]
Engineering Strain state:
[ ε(t)] =[ \begin{matrix}\varepsilon(xx\ )(t)&0&0\\0&-\nu\ast\varepsilon(xx\ )(t)&0\\0&0&-\nu\ast\varepsilon(xx\ )(t)\\\end{matrix}]


True strain:
The deformation gradient will be calculated with given function for displacement in x, y and z directions. In general, it is defined as:

F = Fab ea    eb               with [Fab]= [δab + \frac{du(a)}{dx(b)}]   this will be 3x3 matrix with 9 elements.           
 where u(a) = displacement of material points from initial state to current state 
x(b) = position vector at current state and 
δab = Kronecker delta.
Function of displacement u(a) in x, y and z directions:
	u(x) = displacement function in x direction in uniaxial tension.
u(x) = {(L(t) – L(to)} *  \frac{x}{L(t(o))} = (λ(t) – 1) * x; where  λ(t) = stretch ratio in longitudinal direction during uniaxial tension. 
	u(y) = displacement function in y direction in uniaxial tension.
u(y) = {(W(t) – W(to)} *  \frac{y}{L(t(o))} = m(t) * y; where m(t) = \frac{W\left(t\right)-W(t\left(o\right))}{L(t(o))} = stretch ratio in lateral direction during uniaxial tension. 
	u(z) = displacement function in z direction in uniaxial tension.
u(z) = {(S(t) – S(to)} *  \frac{z}{L(t(o))} = n(t) * z; where n(t) = \frac{S\left(t\right)-S(t\left(o\right))}{L(t(o))} = stretch ratio in lateral direction during uniaxial tension. 

Since poison’s ratio is given so m(t) and n(t) can be calculated in terms of (λ(t))
ν   =  -  \frac{\ lateral\ strain\ }{Longitudinal\ strain}

So, converting the displacement functions in terms of stretch ratio in longitudinal and poison’s ratio.
u(x) = (λ(t) – 1) * x
u(y) = m(t) * y = - ν Wo * (λ(t) -1)
u(z) = m(t) * z =  - ν So * (λ(t) -1)

longitudinal strain = Linear εxx (t) = \frac{L(t)}{L(t(o))}-1 = λ(t) – 1 
Lateral strain = Linear εyy (t) = \frac{W(t)}{W(t(o))}-1\ \ = - \nu εxx (t) and Linear εzz (t) = \frac{S(t)}{S(t(o))}-1\  = - \nu εxx (t)
where = \frac{L(t)}{L(to)} = λ(t) 

m(t) = - ν Wo * (λ(t) -1)
n(t) = - ν So * (λ(t) -1)



Now the [Fab] will be calculated from above functions. It will be 3 * 3 matrix with 9 elements. 
δab = ea    eb     =	 1	 if a == b
			  0	 if a not equal to b
Derivative of u(a) with respect to x(b) will be calculated along with Kronecker delta and then longitudinal and lateral stretches will be calculated. 


[Fab] =[ \begin{matrix}\lambda(t)&0&0\\0&m(t)&0\\0&0&n(t)\\\end{matrix}]

True strain can be calculated from above [Fab]
h(t) = \frac{1}{2}ln((b))
where h(t) = Hencky strain tensor and 
b = Left Cauchy Green tensor with b = F. FT

or [bab] = [Fab] [Fab]T

[bab] =[\begin{matrix}\lambda^2(t)&0&0\\0&m^2(t)&0\\0&0&n^2(t)\\\end{matrix}]

Where m(t) and n(t) can be calculated from poision’s ratio and displacement function relations
True Strain state:
h(t) = [\begin{matrix}ln(\lambda(t))&0&0\\0&ln(m(t))&0\\0&0&ln(n(t))\\\end{matrix}]
True Stress state:
For calculation of true stress, σ (or Cauchy stress), following equation will be used and 
volume ratio (J) will be used. 
Equation determining the relation between true stress, σ (or Cauchy stress) and 1st Piola Kirchoff stress, T (or engineering stress):
σ =  \frac{1}{J} * F . T . FT
Where F = Deformation gradient and 
	J = Volume ratio =  \frac{dV}{dV(o)} = \frac{change\ in\ volume\ in\ current\ state}{change\ in\ volume\ in\ reference\ (initial)\ state}
J can be calculated from the third principal invariant of deformation gradient. Therefore, 
J = I3(F) = determinant(F)
σ(xx) at t = \lambda(t) ^3 * m(t) * n(t) * T(t)
σ(yy) = 0 
σ(zz) = 0
Now True stress state:
[σ (t)] = [ \begin{matrix}\sigma(t)&0&0\\0&0&0\\0&0&0\\\end{matrix}]


Section 1.3: Graphs 
	Stretch ratio vs time 
	Strain vs time
	Engineering strain vs time.
	True strain vs time.
	Engineering strain and true strain vs time in one graph.
	Stress vs time
	Engineering stress vs time.
	True stress vs time.
	Engineering stress and true stress vs time in one graph.
	Stress vs strain.
	Engineering stress vs engineering strain (Hooke's law).
	True Stress vs true strain.
	Engineering stress and true stress vs Stretch ratio in one graph.

Results: 
	Strain state
	Engineering strain state 
	True strain state (or Eulerian - Hencky strain)
	Stress state:
	Engineering stress state (T = 1st Poila Kirchoff stress)
	True stress state (\sigma = Cauchy stress)
 

