
# URDF 文件中坐标的理解（xyz、rpy）
    xyz就是正交坐标xyz（满足右手定则）
    rpy是roll(横滚、以X轴翻转)、Pitch(俯仰、以Y轴翻转)、Yaw（偏航、以Z轴翻转）
    除去root link，其余坐标变化都是以相邻的Joint坐标为依据，进行变换的，也就是以该节点的Parent Link 作为Child Link的节点的坐标，进行变换的

