# -*- encoding: utf-8 -*-
from django.db import models


class Wechat(models.Model):
	nick = models.CharField(u"微信号", max_length=256)
	
	class Meta(object):
		app_label = u"customer"
		

class Customer(models.Model):
	name = models.CharField(u"姓名", max_length=256)
	phonenum = models.CharField(u"手机号码", max_length=32)
	#如果wechat为null，说明该用户尚未绑定微信
	wechat = models.OneToOneField(Wechat, verbose_name=u"微信号", blank=True, null=True)	
	address = models.TextField(u"住址", max_length=512, blank=True, null=True)
	
	class Meta(object):
		app_label = u"customer"

	def __unicode__(self):
		return self.name
