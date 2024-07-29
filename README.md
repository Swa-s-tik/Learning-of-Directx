# # My-Learning-Path-of-C++
# My detailed path of learning 3D rendering and DirectX12 with code and notes!

# Vectors are used to model physical quantities that possess both magnitude and
# direction. Geometrically, we represent a vector with a directed line segment. A vector
# is in standard position when it is translated parallel to itself so that its tail coincides
# with the origin of the coordinate system. A vector in standard position can be
# described numerically by specifying the coordinates of its head relative to a
# coordinate system.
# If u = (ux, uy, uz) and v = (vx, vy, vz), then we have the following vector operations:
# Addition: u + v = (ux + vx, uy + vy, uz + vz)
# Subtraction: u − v = (ux − vx, uy − vy, uz − vz)
# Scalar Multiplication: ku = (kux, kuy, kuz)
# Length: ||u|| = sqrt(x2+y2+z2)
# Normalization: u/||u||
# Dot Product: u.v=||u||||v||cos0= uxvx + uyvy + uzvz
# Cross Product: uXv = (uyvz-uzvy , uzvx-uxvz , uxvy - uyvx)
# We use the DirectX Math XMVECTOR type to describe vectors efficiently in code
# using SIMD operations. For class data members, we use the XMFLOAT2,
# XMFLOAT3, and XMFLOAT4 classes, and then use the loading and storage methods
# to convert back and forth between XMVECTOR and XMFLOATn. Constant vectors
# that require initialization syntax should use the XMVECTORF32 type.
# For efficiency purposes, XMVECTOR values can be passed as arguments to functions
# in SSE/SSE2 registers instead of on the stack. To do this in a platform independent
# way, we use the types FXMVECTOR, GXMVECTOR, HXMVECTOR and CXMVECTOR
# for passing XMVECTOR parameters. Then the rule for passing XMVECTOR parameters
# is that the first three XMVECTOR parameters should be of type FXMVECTOR; the
# fourth XMVECTOR should be of type GXMVECTOR; the fifth and sixth XMVECTOR
# parameter should be of type HXMVECTOR; and any additional XMVECTOR
# parameters should be of type CXMVECTOR.
# The XMVECTOR class overloads the arithmetic operators to do vector addition,
# subtraction, and scalar multiplication. Moreover, the DirectX Math library provides
# the following useful functions for computing the length of a vector, the squared
# length of a vector, computing the dot product of two vectors, computing the cross
# product of two vectors, and normalizing a vector:
# XMVECTOR XM_CALLCONV XMVector3Length(FXMVECTOR V);
# XMVECTOR XM_CALLCONV XMVector3LengthSq(FXMVECTOR V);
# XMVECTOR XM_CALLCONV XMVector3Dot(FXMVECTOR V1,
# FXMVECTOR V2);
# XMVECTOR XM_CALLCONV XMVector3Cross(FXMVECTOR V1,
# FXMVECTOR V2);
# XMVECTOR XM_CALLCONV XMVector3Normalize(FXMVECTOR V);
# An m × n matrix M is a rectangular array of real numbers with m rows and n
# columns. Two matrices of the same dimensions are equal if and only if their
# corresponding components are equal. We add two matrices of the same dimensions
# by adding their corresponding elements. We multiply a scalar and a matrix by
# multiplying the scalar with every element in the matrix.
# If A is a m × n matrix and B is a n × p matrix, then the product AB is defined and is a
# m × p matrix C, where the ijth entry of the product C is given by taking the dot
# product of the ith row vector in A with the jth column vector in B, that is,
# Cij = Ai* . B*j
# .
# Matrix multiplication is not commutative (i.e., AB ≠ BA, in general). Matrix
# multiplication is associative: (AB)C = A(BC).
# The transpose of a matrix is found by interchanging the rows and columns of the
# matrix. Thus the transpose of an m × n matrix is an n × m matrix. We denote the
# transpose of a matrix M as MT
# .
# The identity matrix is a square matrix that has zeros for all elements except along the
# main diagonal, and the elements along the main diagonal are all ones.
# The determinant, det A, is a special function which inputs a square matrix and
# outputs a real number. A square matrix A is invertible if and only if det A ≠ 0. The
# determinant is used in the formula for computing the inverse of a matrix.
# Multiplying a matrix with its inverse results in the identity matrix: MM−1 = M−1M =
# I. The inverse of a matrix, if it exists, is unique. Only square matrices have inverses
# and even then, a square matrix may not be invertible. The inverse of a matrix can be
# computed with the formula: , where is the adjoint (transpose of the cofactor matrix of
# A).
# We use the DirectX Math XMMATRIX type to describe 4 × 4 matrices efficiently in
# code using SIMD operations. For class data members, we use the XMFLOAT4X4
# class, and then use the loading (XMLoadFloat4x4) and storage
# (XMStoreFloat4x4) methods to convert back and forth between XMMATRIX and
# XMFLOAT4X4. The XMMATRIX class overloads the arithmetic operators to do matrix
# addition, subtraction, matrix multiplication, and scalar multiplication. Moreover, the
# DirectX Math library provides the following useful matrix functions for computing
# the identity matrix, product, transpose, determinant, and inverse:
# XMMATRIX XM_CALLCONV XMMatrixIdentity();
# XMMATRIX XM_CALLCONV XMMatrixMultiply(FXMMATRIX A,
# CXMMATRIX B);
# XMMATRIX XM_CALLCONV XMMatrixTranspose(FXMMATRIX M);
# XMVECTOR XM_CALLCONV XMMatrixDeterminant(FXMMATRIX
# M);
# XMMATRIX XM_CALLCONV XMMatrixInverse(XMVECTOR*
# pDeterminant, FXMMATRIX M);
# Direct3D can be thought of as a mediator between the programmer and the graphics
# hardware. For example, the programmer calls Direct3D functions to bind resource
# views to the hardware rendering pipeline, to configure the output of the rendering
# pipeline, and to draw 3D geometry.
# Component Object Model (COM) is the technology that allows DirectX to be
# language independent and have backwards compatibility. Direct3D programmers
# don’t need to know the details of COM and how it works; they need only to know
# how to acquire COM interfaces and how to release them.
# A 1D texture is like a 1D array of data elements, a 2D texture is like a 2D array of
# data elements, and a 3D texture is like a 3D array of data elements. The elements of a
# texture must have a format described by a member of the DXGI_FORMAT
# enumerated type. Textures typically contain image data, but they can contain other
# data, too, such as depth information (e.g., the depth buffer). The GPU can do special
# operations on textures, such as filter and multisample them.
# To avoid flickering in animation, it is best to draw an entire frame of animation into
# an off-screen texture called the back buffer. Once the entire scene has been drawn to
# the back buffer for the given frame of animation, it is presented to the screen as one
# complete frame; in this way, the viewer does not watch as the frame gets drawn.
# After the frame has been drawn to the back buffer, the roles of the back buffer and
# front buffer are reversed: the back buffer becomes the front buffer and the front
# buffer becomes the back buffer for the next frame of animation. Swapping the roles
# of the back and front buffers is called presenting. The front and back buffer form a
# swap chain, represented by the IDXGISwapChain interface. Using two buffers
# (front and back) is called double buffering.
# Assuming opaque scene objects, the points nearest to the camera occlude any points
# behind them. Depth buffering is a technique for determining the points in the scene
# nearest to the camera. In this way, we do not have to worry about the order in which
# we draw our scene objects.
# In Direct3D, resources are not bound to the pipeline directly. Instead, we bind
# resources to the rendering pipeline by specifying the descriptors that will be
# referenced in the draw call. A descriptor object can be thought of as lightweight
# structure that identifies and describes a resource to the GPU. Different descriptors of
# a single resource may be created. In this way, a single resource may be viewed in
# different ways; for example, bound to different stages of the rendering pipeline or
# have its bits interpreted as a different DXGI_FORMAT. Applications create descriptor
# heaps which form the memory backing of descriptors.
