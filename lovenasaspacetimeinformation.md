In this script, we calculate the distance between the asteroid and the ISS using the Euclidean distance formula, and check if the distance is less than a certain threshold (collision_dist). If a potential collision is detected, a warning message is printed. Otherwise, the script prints out the space-time positions and velocities of the asteroid and the ISS. This can be used by the ISS crew to monitor potential collisions and take appropriate measures to avoid them.
```import numpy as np

# Define the position of the asteroid in Cartesian coordinates
ax = 2000    # km
ay = -3000    # km
az = 4000    # km

# Define the time at which the position is given
t = 0    # seconds

# Define the gravitational constant
G = 6.67430e-11    # m^3/(kg*s^2)

# Define the mass of the Earth and the ISS
M_earth = 5.972e24    # kg
M_iss = 419725    # kg

# Define the position and velocity of the ISS in STPI format
iss_pos = np.array([t, 0, 6771*1000, 0])
iss_vel = np.array([0, 0, 0, 0])

# Calculate the distance between the asteroid and the ISS
r_ast_iss = np.sqrt((ax - iss_pos[1])**2 + (ay - iss_pos[2])**2 + (az - iss_pos[3])**2) * 1000    # m

# Calculate the magnitude of the asteroid's position vector
r_ast = np.sqrt(ax**2 + ay**2 + az**2) * 1000    # m

# Calculate the velocity components of the asteroid
v_ast_x = -np.sqrt(G*M_earth/r_ast) * ay/r_ast * 1000    # m/s
v_ast_y = np.sqrt(G*M_earth/r_ast) * ax/r_ast * 1000    # m/s
v_ast_z = 0    # m/s

# Define the space-time position and velocity vectors of the asteroid
ast_pos = np.array([t, ax*1000, ay*1000, az*1000])
ast_vel = np.array([0, v_ast_x, v_ast_y, v_ast_z])

# Check for potential collision with the ISS
collision_dist = 200*1000    # m
if r_ast_iss < collision_dist:
    print("WARNING: Potential collision with the ISS detected!")
else:
    print("No potential collisions detected.")

# Print the results
print("Asteroid space-time position: ", ast_pos)
print("Asteroid velocity: ", ast_vel)
print("ISS space-time position: ", iss_pos)
print("ISS velocity: ", iss_vel)
```
