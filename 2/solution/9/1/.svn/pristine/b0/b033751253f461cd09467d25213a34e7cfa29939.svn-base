import matplotlib.pyplot as plt
import math
import numpy as np


#Generate line points
def line_gen(A,B):
  len =10
  dim = A.shape[0]
  x_AB = np.zeros((dim,len))
  lam_1 = np.linspace(0,1,len)
  for i in range(len):
    temp1 = A + lam_1[i]*(B-A)
    x_AB[:,i]= temp1.T
  return x_AB

#GIVEN POINTS

a=np.array([1,1])
b=np.array([3,5])
c=np.array([-2,4])
d=np.array([-1,-5])


#Direction Vectors
print(b-a,c-b,d-c,a-d)
one_vec = np.array([[1],[1],[1]])
print(one_vec)
ab=np.vstack((b-a,d-b,a-d))
print(ab)
chk_matrix = np.concatenate((ab,one_vec), axis=1)
#print(ab)
#chk_matrix=np.vstack(([b-a,1],[a-d,1],[d-b,1])).T
print(chk_matrix)
rank_matrix = np.linalg.matrix_rank(chk_matrix)
print(rank_matrix)

# Area of Quadrilateral Function Definition
def area_quad(a,b,c,d):
  area_tri1 = area_triangle(a,b,c)
  print(area_tri1)
  area_tri2 = area_triangle(a,c,d)
  print(area_tri2)
  area_quad_val = area_tri1 + area_tri2
  return area_quad_val

#Area of a triangle using Determinant of Matrix
def area_triangle(a,b,c):
  det_matrix = np.array([[a[0],a[1],1],[b[0],b[1],1],[c[0],c[1],1]])
  print(det_matrix)
  area_tri = 0.5 * int(np.linalg.det(det_matrix))
  return area_tri
  #area_tri = 0.5 * det

#LINE GENERATIONS FOR PLOT

#SIDES OF A QUADRILATERAL

x_ab = line_gen(a,b)
#print(x_ab)
x_bc = line_gen(b,c)
x_cd = line_gen(c,d)
x_da = line_gen(d,a)

# DIAGONALS OF QUADRILATERAL

x_ac = line_gen(a,c)
x_bd = line_gen(b,d)

#Area of a Quadrilateral Calculation after Collinearity Check
if rank_matrix < 3: 
    print("Points A, B, and D are collinear. They dont form a Quadrilateral.")
else:
  area_val = area_quad(a,b,c,d)
  print(area_val)
  
# PLOTTING THE LINES

plt.plot(x_ab[0,:],x_ab[1,:], label="$AB$")
plt.plot(x_bc[0,:],x_bc[1,:], label="$BC$")
plt.plot(x_cd[0,:],x_cd[1,:], label="$CD$")
plt.plot(x_da[0,:],x_da[1,:], label="$DA$")
plt.plot(x_ac[0,:],x_ac[1,:], label="$AC$")
plt.plot(x_bd[0,:],x_bd[1,:], label="$BD$")

#ANNOTATIONS IN GRAPH
quad_coords = np.vstack((a,b,c,d)).T
plt.scatter(quad_coords[0,:], quad_coords[1,:])
vert_labels = ['A','B','C','D']
for i, txt in enumerate(vert_labels):
    plt.annotate(txt, # this is the text
                 (quad_coords[0,i], quad_coords[1,i]), # this is the point to label
                 textcoords="offset points", # how to position the text
                 xytext=(0,10), # distance from text to points (x,y)
                 ha='center') # horizontal alignment can be left, right or center

plt.xlabel('$x$')
plt.ylabel('$y$')
plt.legend(loc='best')
plt.grid()
plt.xlim(-10,10)
plt.ylim(-10,10)
plt.savefig('QUAD.png')
plt.show()
