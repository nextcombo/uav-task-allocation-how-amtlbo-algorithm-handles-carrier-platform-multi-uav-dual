# UAV Task Allocation: How AMTLBO Algorithm Handles "Carrier Platform + Multi-UAV" Dual Heterogeneous Task Allocation? [Python Code Included]

Abstract: Heterogeneous unmanned aerial vehicles (UAVs) have been widely used in modern warfare, but their limited endurance restricts the operational range. This issue can be effectively addressed by carrier or ship-based platforms such as large transport aircraft and aircraft carriers. However, existing research has paid less attention to this problem. This paper investigates the Coordinated Multi-UAV Task Allocation with Enhanced Carrier Platform (CPMCTA) problem, which involves both UAVs and carrier platforms, while considering the risk of approaching unattacked targets (AUTIR), an aspect often overlooked in traditional studies, to enhance task execution safety. A novel CPMCTA model that incorporates task priority, obstacles, AUTIR, and heterogeneity is first established. To efficiently solve this problem, an adaptive self-motivated teaching and learning optimization algorithm (AMTLBO) is proposed, integrating multi-teacher mechanisms, adaptive learning rates, and self-motivation. Simulation results across multiple scenarios demonstrate that AMTLBO outperforms other six advanced algorithms in terms of optimization performance, while also validating the necessity of considering AUTIR. The simulation animations can be viewed through the Bilibili video link for a more intuitive demonstration.
Introduction: Unmanned aerial vehicles (UAVs) are characterized by high adaptability, stealthiness, safety, and cost-effectiveness, enabling them to replace manned equipment for various complex tasks and finding wide applications in military and civilian sectors. Due to limitations in load and endurance, single UAVs struggle to adapt to modern complex battlefield environments. Inspired by the phenomenon of animal group behavior in nature, the concept of Multi-UAV Coordinated Task Assignment (MCTA) emerged. Through leveraging member collaboration capabilities, MCTA offers higher flexibility, adaptability, and robustness, gradually replacing single UAVs for task execution.
MCTA is essentially a combinatorial optimization problem under multi-variables, multi-objectives, multi-constraints, and multi-source information fusion. It requires consideration of task feasibility, priority, coordination, and flight paths within restricted airspace. Building an appropriate mathematical model is challenging due to its complexity, and the problem exhibits NP-hard characteristics. Solving algorithms face exponential time complexity growth with problem scale, making the development of suitable mathematical models and efficient solution algorithms crucial.
Existing MCTA research predominantly employs mixed integer linear programming modeling, with the Collaborative Multi-Task Assignment Problem (CMTAP) being particularly notable for accurately modeling heterogeneity in MCTA. However, the presence of heterogeneity increases the difficulty of solving. Concurrently, most existing studies overlook the role of carrier platforms, yet in cross-regional joint operations, utilizing heterogeneous carrier platforms for takeoff and landing drones can expand mission scope and facilitate remote combat. Additionally, current research generally neglects AUTIR around unattended targets, which escalates operational risks.
In response to the above shortcomings, this paper conducts research from three aspects: firstly, extending the heterogeneity of drones only to that of both drones and carrier platforms, thereby establishing a new CPMCTA model; secondly, modeling AUTIR and setting penalty terms in the objective function to enhance task safety; thirdly, designing an AMTLBO algorithm with integrated multi-exploration mechanisms, which outperforms existing advanced methods in optimization performance.
Task background and method task background problem description in CPMCTA, heterogeneous carrier platforms (such as aircraft carriers, large transport aircraft, land platforms) carry drones to the battlefield, and perform collaborative tasks based on the battlefield situation. The core elements involved include:
•  
Heterogeneous carrier platform collection P: contains different types (land L, sea O, air A), moving at a fixed speed in a straight line.
•  
Heterogeneous UAV fleet: Divided into reconnaissance (R), ammunition (M), combat (C) types, with different combat capabilities and parameters (ammunition load, minimum turning radius, average speed);
•  
Target set T: static targets, each target must be executed in the order of "classification (C) - attack (A) - verification (V)".
•  
Battlefield Obstacles: Including circular and convex polygon no-fly zones (such as radar, mountainous areas, air defense strike zones, etc.), drone flight requires avoidance of obstacles.
Task execution must meet path planning and coordination requirements: Use the visibility graph method for obstacle avoidance path planning, and coordinate task priorities through the waiting circle method in the Doob's path to ensure that low-priority tasks are executed after high-priority tasks.
Mathematical model•
Objective function: Minimize the sum of total execution time (F1) and AUTIR threat penalty (F2), where F1 is the maximum execution time of all UAV missions, and F2 is calculated based on the proximity to unattacked targets (the closer the target, the greater the punishment);
•
Constraint conditions: UAV payload constraints (maximum number of attack missions not exceeding the payload capacity), battlefield obstacle avoidance constraints (flight paths do not cross no-fly zones), task constraints (all tasks must be executed and meet priority levels), carrier platform constraints (UAV takes off from CP and returns to CP).
Solution method Discrete teaching and learning optimization algorithm (Discrete TLBO) adapted to CPMCTA's discrete characteristics, improves on traditional TLBO by discretization:
•
Encoding method: A 3-row ×3N_T-column encoding structure, corresponding to objectives, task types (1=C, 2=A, 3=V), UAV, with initialization ensuring task capability and payload constraints are met;
•
Crossover mutation: Single-point crossover operation facilitates information exchange between solutions, and two mutation operations (task execution UAV swapping and adjusting UAV task sequence) are designed to escape local optima;
•
Lockout release: Based on logic, a lockout release method is used to resolve deadlocks caused by violations of task sequence constraints.
Adaptive self-motivated teaching and learning optimization algorithm (AMTLBO) addresses the shortcomings of discrete TLBO by introducing three improvements:
•
Multi-teacher mechanism: Dynamically adjust the number of teachers according to the iterative process, ensuring population diversity at the beginning, and improving convergence efficiency later;
•
Adaptive learning rate: Adjust the learning rate dynamically based on the gap between the objective function values of learners and teachers, matching different levels of learners' crossover strategies;
Self-Induced Phase: The introduction of mutation operations simulates the self-learning process, enhancing population diversity and avoiding premature convergence.
Population State Judgment: By analyzing the relationship between the mean and median of the population, dynamic selection is made to enter the teaching or learning phase, improving computational efficiency.
Conclusion: This paper proposes an adaptive Self-Induced Learning Optimization Algorithm (AMTLBO) for solving the dual heterogeneous multi-UAV Coordinated Task Assignment (CPMCTA) problem considering carrier platform delivery and unattacked target proximity induced risk (AUTIR). The introduction of heterogeneous carrier platforms enhances the task execution capability of UAVs, while the modeling of AUTIR fills the gap in current research on task safety considerations - by setting a threat penalty term in the objective function, effectively reducing the risk of UAVs performing tasks.
The AMTLBO algorithm solves the problem of traditional algorithms easily falling into local optima through multiple teacher mechanisms, adaptive learning rates, and self-induction mechanisms. Simulation results show that compared to six other advanced heuristic algorithms, this algorithm performs better in terms of optimization performance and stability, and also verifies the effectiveness of the penalty-based objective function in mitigating AUTIR.
Future research will focus on three aspects: firstly, exploring deep reinforcement learning frameworks to address the high-quality solution needs of large-scale MCTA problems; secondly, developing dynamic task reassignment strategies to adapt to real-time disturbance scenarios such as device failures and new targets; thirdly, perfecting the modeling of UAV takeoff and landing recovery processes for carrier platforms, building a "takeoff - combat - recovery" full cycle optimization model.
End

## Images

![(Drone Task Allocation)How AMTLBO algorithm handles the dual heterogeneous task allocation of "carrier platform + multiple drones"? [Attached Python code]](01.jpg)
![(Drone Task Allocation)How AMTLBO algorithm handles the dual heterogeneous task allocation of "carrier platform + multiple drones"? [Attached Python code]](02.jpg)
![(Drone Task Allocation)How AMTLBO algorithm handles the dual heterogeneous task allocation of "carrier platform + multiple drones"? [Attached Python code]](03.jpg)
![(Drone Task Allocation)How AMTLBO algorithm handles the dual heterogeneous task allocation of "carrier platform + multiple drones"? [Attached Python code]](04.jpg)
![(Drone Task Allocation)How AMTLBO algorithm handles the dual heterogeneous task allocation of "carrier platform + multiple drones"? [Attached Python code]](05.jpg)
![(Drone Task Allocation)How AMTLBO algorithm handles the dual heterogeneous task allocation of "carrier platform + multiple drones"? [Attached Python code]](06.jpg)
![(Drone Task Allocation)How AMTLBO algorithm handles the dual heterogeneous task allocation of "carrier platform + multiple drones"? [Attached Python code]](07.jpg)
![(Drone Task Allocation)How AMTLBO algorithm handles the dual heterogeneous task allocation of "carrier platform + multiple drones"? [Attached Python code]](08.jpg)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
