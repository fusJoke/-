```sql
CREATE TABLE `aum_home_product` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT COMMENT 'id',
  `uid` int(11) unsigned NOT NULL COMMENT '用户表（aum_home_user）id',
  `brand_id` int(11) unsigned NOT NULL COMMENT '品牌表（aum_home_brand）id',
  `name` varchar(200) NOT NULL DEFAULT '' COMMENT '产品名称',
  `name_en` varchar(200) NOT NULL DEFAULT '' COMMENT '产品名称-英文',
  `product_code` varchar(100) NOT NULL DEFAULT '' COMMENT '产品编码',
  `price` decimal(9,2) unsigned NOT NULL DEFAULT '0.00' COMMENT '零售价格',
  `spec` varchar(255) NOT NULL DEFAULT '' COMMENT '产品规格',
  `spec_en` varchar(255) NOT NULL DEFAULT '' COMMENT '产品规格-英文',
  `img` varchar(255) NOT NULL DEFAULT '' COMMENT '产品图片',
  `introduce` text COMMENT '产品介绍',
  `introduce_en` text COMMENT '产品介绍-英文',
  `details_img` varchar(1000) NOT NULL DEFAULT '' COMMENT '详情图片',
  `details_img_en` varchar(1000) NOT NULL DEFAULT '' COMMENT '详情图片-英文',
  `is_check` tinyint(1) unsigned NOT NULL DEFAULT '0' COMMENT '是否审核  0：未审核  1：审核通过  2：审核不通过  ',
  `check_time` int(10) unsigned NOT NULL DEFAULT '0' COMMENT '审核时间',
  `check_remarks` varchar(255) NOT NULL DEFAULT '' COMMENT '审核备注',
  `c_time` int(10) unsigned NOT NULL COMMENT '创建时间',
  `u_time` int(10) unsigned NOT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`),
  KEY `uid` (`uid`) USING BTREE,
  KEY `brand_id` (`brand_id`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='官网-产品表';


```



```

```

