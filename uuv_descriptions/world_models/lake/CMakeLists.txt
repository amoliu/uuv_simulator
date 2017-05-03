set(MODEL_NAME lake)

set (files
  model.sdf
  model.config
  LakeBottom.dae
  WaterSurface.dae
)
install(FILES ${files} DESTINATION ${CMAKE_INSTALL_PREFIX}/share/gazebo-${GAZEBO_VERSION}/models/${MODEL_NAME})
