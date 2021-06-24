# dasdata

表结构：
CREATE TABLE `t_das_account` (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '数据密级S1,id',
  `owner_address` varchar(64) COMMENT '数据密级S1,地址',
  `owner_pubkey_hash` varchar(64) COMMENT '数据密级S1,owner',
  `account` varchar(64) COMMENT '数据密级S1,账户',
  `manager_pubkey_hash` varchar(64) COMMENT '数据密级S1,manager',
  `expired_at` timestamp COMMENT '数据密级S1,过期时间',
  `registered_at` timestamp COMMENT '数据密级S1,注册时间',
  `status` int COMMENT '数据密级S1,状态 0x00 means normal, 0x01 means being sold, 0x02 means being auctioned.     status: Uint8,',
  `records` varchar(500) COMMENT '数据密级S1,记录',
  `block_number` int COMMENT '数据密级S1,区块高度',
  `create_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '数据密级S1,创建时间',
  `update_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '数据密级S1,最近更新时间',
  `is_delete` smallint NOT NULL DEFAULT 0 COMMENT '数据密级S1,逻辑删除',
  PRIMARY KEY(`id`),
  INDEX `idx_t_das_account_ctime`(`create_time`) USING BTREE COMMENT '创建时间索引',
  INDEX `idx_t_das_account_utime`(`update_time`) USING BTREE COMMENT '更新时间索引'
) ENGINE = InnoDB CHARACTER SET = utf8mb4 COMMENT = '数据密级S1,das账号表';
